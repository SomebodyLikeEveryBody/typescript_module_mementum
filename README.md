# Typescript module mementum
Typescript memetum to remember how to split code into several files without using module feature witch prohibit the local use with file:// protocole because of the Same Origin Policy.

It's a pity that javascript modules are always loaded using http instead of the currently used procole (http if the application uses http://, file if the applications uses file:// etc) as it does for all html ressources.

# Step 1
Module file's code is encapsulated into a namespace with the name of the module. Example:

```javascript
/* myModule.ts file */
namespace myModule {
    export let pouetValue = 42;
    export function sayCoucou(pName: string = 'Michel') {
        console.log('Coucou ' + pName);
    }
}
```

# Step 2
When we need to use external features in a ts file, we do it directly without importing, as follow:
```javascript
/* main.js file */
myModule.sayCoucou();
```

# Step 3
We compile all in a standalone file to load it in the html web page later:
```
tsc --outFile ./js.js ./main.ts ./myModule.ts
```

# Step 4
We include it in the html page
```html
<script src="./js.js"></script>
```

Voila.
