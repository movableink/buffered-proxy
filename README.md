BufferedProxy
=============

Proxy object for easy rollbacks.

Usage
=====

```
var FooController = Ember.ObjectController.extend({
  bufferedContent: function() {
    return Em.ObjectProxy.extend(BufferedProxy).create({
      content: this.get('content')
    });
  }.property('content'),

  actions: {
    save: function() {
      this.get('bufferedContent').applyBufferedChanges();
    },

    cancel: function() {
      this.get('bufferedContent').discardBufferedChanges();
    }
  }
});
```

About
=====

Written by Cory Forsyth, adapted for Bower by Michael Nutt.
