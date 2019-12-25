## Public and Private API ##

_API documentation automatically generated by [docmeteor](https://github.com/raix/docmeteor)._

***

__File: ["common.js"](common.js) Where: {client|server}__

***

#############################################################################

COLLECTION FS

#############################################################################
-

### <a name="FS.Collection"></a>new *fs*.Collection(name, options)&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __Collection__ is defined in `FS`*

__Arguments__

* __name__ *{string}*  

 A name for the collection

* __options__ *{Object}*  
    * __stores__ *{[FS.StorageAdapter[]](#FS.StorageAdapter[])}*  

    An array of stores in which files should be saved. At least one is required.

    * __filter__ *{Object}*  (Optional)

    Filter definitions

    * __chunkSize__ *{Number}*  (Optional, Default = 131072)

    Override the chunk size in bytes for uploads and downloads


__Returns__  *{undefined}*



> ```FS.Collection = function(name, options) { ...``` [common.js:17](common.js#L17)


***

__File: ["api.common.js"](api.common.js) Where: {client|server}__

***

### <a name="FS.Collection.prototype.insert"></a>*fsCollection*.insert(fileRef, [callback])&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __insert__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __fileRef__ *{[FS.File](#FS.File)|[File](#File)}*  

 File data reference

* __callback__ *{function}*  (Optional)

 Callback `function(error, fileObj)`


__Returns__  *{FS.File}*
The `file object`
[Meteor docs](http://docs.meteor.com/#insert)

> ```FS.Collection.prototype.insert = function(fileRef, callback) { ...``` [api.common.js:8](api.common.js#L8)


-

### <a name="FS.Collection.prototype.update"></a>*fsCollection*.update(selector, modifier, [options], [callback])&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __update__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __selector__ *{[FS.File](#FS.File)|object}*  
* __modifier__ *{object}*  
* __options__ *{object}*  (Optional)
* __callback__ *{function}*  (Optional)
[Meteor docs](http://docs.meteor.com/#update)

> ```FS.Collection.prototype.update = function(selector, modifier, options, callback) { ...``` [api.common.js:71](api.common.js#L71)


-

### <a name="FS.Collection.prototype.remove"></a>*fsCollection*.remove(selector, [callback])&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __remove__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __selector__ *{[FS.File](#FS.File)|object}*  
* __callback__ *{Function}*  (Optional)
[Meteor docs](http://docs.meteor.com/#remove)

> ```FS.Collection.prototype.remove = function(selector, callback) { ...``` [api.common.js:92](api.common.js#L92)


-

### <a name="FS.Collection.prototype.findOne"></a>*fsCollection*.findOne(selector)&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __findOne__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __selector__ *{[selector](http://docs.meteor.com/#selectors)}*  
[Meteor docs](http://docs.meteor.com/#findone)
Example:
```js
var images = new FS.Collection( ... );
// Get the file object
var fo = images.findOne({ _id: 'NpnskCt6ippN6CgD8' });
```

> ```FS.Collection.prototype.findOne = function(selector) { ...``` [api.common.js:122](api.common.js#L122)


-

### <a name="FS.Collection.prototype.find"></a>*fsCollection*.find(selector)&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __find__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __selector__ *{[selector](http://docs.meteor.com/#selectors)}*  
[Meteor docs](http://docs.meteor.com/#find)
Example:
```js
var images = new FS.Collection( ... );
// Get the all file objects
var files = images.find({ _id: 'NpnskCt6ippN6CgD8' }).fetch();
```

> ```FS.Collection.prototype.find = function(selector) { ...``` [api.common.js:138](api.common.js#L138)


-

### <a name="FS.Collection.prototype.allow"></a>*fsCollection*.allow(options)&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __allow__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __options__ *{object}*  
    * __download__ *{function}*  

    Function that checks if the file contents may be downloaded

    * __insert__ *{function}*  
    * __update__ *{function}*  
    * __remove__ *{function}*  

    Functions that look at a proposed modification to the database and return true if it should be allowed

    * __fetch__ *{[string]}*  (Optional)

    Optional performance enhancement. Limits the fields that will be fetched from the database for inspection by your update and remove functions

[Meteor docs](http://docs.meteor.com/#allow)
Example:
```js
var images = new FS.Collection( ... );
// Get the all file objects
var files = images.allow({
insert: function(userId, doc) { return true; },
update: function(userId, doc, fields, modifier) { return true; },
remove: function(userId, doc) { return true; },
download: function(userId, fileObj) { return true; },
});
```

> ```FS.Collection.prototype.allow = function(options) { ...``` [api.common.js:164](api.common.js#L164)


-

### <a name="FS.Collection.prototype.deny"></a>*fsCollection*.deny(options)&nbsp;&nbsp;<sub><i>Anywhere</i></sub> ###

*This method __deny__ is defined in `prototype` of `FS.Collection`*

__Arguments__

* __options__ *{object}*  
    * __download__ *{function}*  

    Function that checks if the file contents may be downloaded

    * __insert__ *{function}*  
    * __update__ *{function}*  
    * __remove__ *{function}*  

    Functions that look at a proposed modification to the database and return true if it should be denyed

    * __fetch__ *{[string]}*  (Optional)

    Optional performance enhancement. Limits the fields that will be fetched from the database for inspection by your update and remove functions

[Meteor docs](http://docs.meteor.com/#deny)
Example:
```js
var images = new FS.Collection( ... );
// Get the all file objects
var files = images.deny({
insert: function(userId, doc) { return true; },
update: function(userId, doc, fields, modifier) { return true; },
remove: function(userId, doc) { return true; },
download: function(userId, fileObj) { return true; },
});
```

> ```FS.Collection.prototype.deny = function(options) { ...``` [api.common.js:200](api.common.js#L200)


***

__File: ["api.client.js"](api.client.js) Where: {client}__

***

### <a name="_eventCallback"></a>_eventCallback(templateName, selector, dataContext, evt, temp, fsFile)&nbsp;&nbsp;<sub><i>Client</i></sub> ###

*This method is private*

__Arguments__

* __templateName__ *{string}*  

 Name of template to apply events on

* __selector__ *{string}*  

 The element selector eg. "#uploadField"

* __dataContext__ *{object}*  

 The event datacontext

* __evt__ *{object}*  

 The event object { error, file }

* __temp__ *{object}*  

 The template instance

* __fsFile__ *{[FS.File](#FS.File)}*  

 File that triggered the event


> ```var _eventCallback = function fsEventCallback(templateName, selector, dataContext, evt, temp, fsFile) { ...``` [api.client.js:10](api.client.js#L10)


-

### <a name="_eachFile"></a>_eachFile(files, metadata, callback)&nbsp;&nbsp;<sub><i>Client</i></sub> ###

*This method is private*

__Arguments__

* __files__ *{array}*  

 List of files to iterate over

* __metadata__ *{object}*  

 Data to attach to the files

* __callback__ *{function}*  

 Function to pass the prepared `FS.File` object


> ```var _eachFile = function(files, metadata, callback) { ...``` [api.client.js:36](api.client.js#L36)


-

### <a name="FS.Collection.acceptDropsOn"></a>*fsCollection*.acceptDropsOn(templateName, selector, [metadata])&nbsp;&nbsp;<sub><i>Client</i></sub> ###

*This method __acceptDropsOn__ is defined in `FS.Collection`*

__Arguments__

* __templateName__ *{string}*  

 Name of template to apply events on

* __selector__ *{string}*  

 The element selector eg. "#uploadField"

* __metadata__ *{object|function}*  (Optional)

 Data/getter to attach to the file objects


Using this method adds an `uploaded` and `uploadFailed` event to the
template events. The event object contains `{ error, file }`

Example:
```css
.dropzone {
border: 2px dashed silver;
height: 5em;
padding-top: 3em;
-webkit-border-radius: 8px;
-moz-border-radius: 8px;
-ms-border-radius: 8px;
-o-border-radius: 8px;
border-radius: 8px;
}
```
```html
<template name="hello">
Choose file to upload:<br/>
<div id="dropzone" class="dropzone">
<div style="text-align: center; color: gray;">Drop file to upload</div>
</div>
</template>
```
```js
Template.hello.events({
'uploaded #dropzone': function(event, temp) {
console.log('Event Uploaded: ' + event.file._id);
}
});
images.acceptDropsOn('hello', '#dropzone');
```

> ```FS.Collection.prototype.acceptDropsOn = function(templateName, selector, metadata) { ...``` [api.client.js:99](api.client.js#L99)


-

### <a name="FS.Collection.acceptUploadFrom"></a>*fsCollection*.acceptUploadFrom(templateName, selector, [metadata])&nbsp;&nbsp;<sub><i>Client</i></sub> ###

*This method __acceptUploadFrom__ is defined in `FS.Collection`*

__Arguments__

* __templateName__ *{string}*  

 Name of template to apply events on

* __selector__ *{string}*  

 The element selector eg. "#uploadField"

* __metadata__ *{object|function}*  (Optional)

 Data/getter to attach to the file objects


Using this method adds an `uploaded` and `uploadFailed` event to the
template events. The event object contains `{ error, file }`

Example:
```html
<template name="hello">
Choose file to upload:<br/>
<input type="file" id="files" multiple/>
</template>
```
```js
Template.hello.events({
'uploaded #files': function(event, temp) {
console.log('Event Uploaded: ' + event.file._id);
}
});
images.acceptUploadFrom('hello', '#files');
```

> ```FS.Collection.prototype.acceptUploadFrom = function(templateName, selector, metadata) { ...``` [api.client.js:156](api.client.js#L156)

