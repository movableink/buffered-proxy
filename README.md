BufferedProxy
=============

Proxy object for easy rollbacks.

Usage
=====

```
var FooController = Ember.ObjectController.extend({
  bufferedContent: function() {
    return Em.ObjectProxy.extend(BufferedProxy).create({
      content: @get('content')
    });
  }.property('content'),

  actions: {
    save: function() {
      @get('bufferedContent').applyBufferedChanges()
    },

    cancel: function() {
      @get('bufferedContent').discardBufferedChanges()
    }
  }
});
```

About
=====

Written by Cory Forsyth, adapted for Bower by Michael Nutt.
