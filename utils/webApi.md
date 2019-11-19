# WEB API

[WEB API - SCOTCH](https://scotch.io/tutorials/get-to-know-the-page-visibility-api)

**1.VISIBILITY CHANGE / VISIBILITY WEB API**

> Used to check the tab is active/rendering/pre-rendering/about to close/hidden

​       document.hidden - **FALSE** - if tab is active 

​                   					**TRUE** - if tab is not active 

 **document.visibilityState** - has states of 

- **visible**: means the tab is visible or has focus.
- **prerender**: the page has loaded but the user has not viewed it.
- **hidden**: page is not visible on any screen.
- **unloaded**: means the user is about to close the current page

#### Example

```js
document.addEventListener('visibilitychange', function () {
  if (document.hidden) {
    // stop running expensive task
  } else {
    // page has focus, begin running task
  }
});
```

 ```js
document.addEventListener('visibilitychange', function () {
    if (document.visibilityState === 'unloaded') {
        triggerNewsletterSignupForm();
    }
});
 ```



**2.ONLINE STATE**

> **Will tell the online / offline status of browser**

​		navigator.onLine - **ONLINE / OFFLINE** 

```js
window.addEventListener('online', tfn);
window.addEventListener('offline', tfn);
fn tfn(e) {
    console.log(e.type);
}
```



**3.VIBRATION API**

`navigator.vibrate(1000);` // vibrate for 1s

`navigator.vibrate(0);`   // stop vibration

`navigator.vibrate([250, 100, 100, 250]);

**250 -** vibrate 250ms 

**100** -wait 

**100 -** vibrate 100ms 

**250 -** wait 

**4.DEVICE ORIENTATION**

```js
window.addEventListener('deviceorientation', changeOr(e)=>{
  console.log(e.alpha, e.beta, e.gamma);
});
```

 

**5.CLIPBOARD**

> To Perform cut, copy, paste,we must have click event

**SELECT**

`ele.setSelectionRange(0, length);`

**COPY**

`document.execCommand('copy');`

**PASTE**

`event.clipboard.getData('plain/text');`



**6.AMBIENT LIGHT**

> exposes the sensor data that captures the light intensity

 ```js
window.addEventListener('devicelight', (e)=>{
  console.log(e.value + 'LUX');
});
 ```

 

**7.BATTERY STATUS**

> allows website to access the battery information of the device

 ```js
navigator.getBattery().then((battery)=>{
  console.log(battery);
  battery.addEventListener('levelchange', ()=>{
    console.log(this.level);
  });
});
 ```



**8.web assembly, web VR, GAMEPAD -** used to detect the controller / jot stick is connected 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 