## RGB Bulb Example

```javascript
const TuyaDevice = require('tuyapi');

let tuya = new TuyaDevice({
    id: 'xxxxxxxxxxxxxxxxxxxx',
    key: 'xxxxxxxxxxxxxxxx'
});

//Define some bulb parameters
var bulbOff = { 1: false };
var bulbOn = { 1: true };
var bulbWhite = { "1": true, "2": "white", "3": 255, "4": 255 };
var bulbNight = { "1": true, "2": "scene", "6": "bd76000168ffff" }


tuya.resolveIds().then(() => {

    //Set with an object
    tuya.set({ set: bulbNight }).then(result => {
        console.log('Result of setting status to night: ' + result);
    });

    //Set device off with standard syntax
    tuya.set({ set: false }).then(result => {
        console.log('Result of setting status to false: ' + result);
    });

    //Set device on with standard syntax
    tuya.set({ set: true }).then(result => {
        console.log('Result of setting status to true: ' + result);
    });

    //Set device mode using dps element 2
    tuya.set({ set: 'white', dps: 2 }).then(result => {
        console.log('Result of setting status to white: ' + result);
    });

});
```