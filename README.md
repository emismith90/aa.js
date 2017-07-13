## What is aa.js

Truly an 'atomic' (2.85 KB) javascript application framework.

## What is inside the box

- Event aggregator by injecting ['$aquarium'] ([aquarium.js](https://github.com/emismith90/aquarium.js))
- Dependency injection by default and programatically by injecting ['$injector'] 

## Usage

```javascript
var app = new AtomicApp();

app.use('jquery', jQuery)
   .use('serviceA', [function () {
        return {
            greeting: function (name) {
                return 'Hello ' + name;
            }
        };
   }])
   .use('serviceB', ['serviceA', function (a) {
        return {
            print: function () {
                console.log(a.greeting('Hung.Le'));
            }
        }
   }])
   .run('main', ['jquery', 'serviceB', '$injector', function ($$, b, $injector) {
        b.print();
        
        if ($$) {
            // jQuery is loaded  
            alert("jQuery!");
        } 
        
        var $aquarium = $injector.resolve('$aquarium');
   }]);
```

## Released under the MIT license
