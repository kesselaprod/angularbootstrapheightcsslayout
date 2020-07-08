# Angular Bootstrap Height CSS Layout
Wrapperless angular bootstrap html5 tag layout with css for a sticky footer and dynamic content adapting row/col height. Working in all browsers on mobile and desktop with the latest angular and bootstrap versions installed using **angular cli** and **npm**.

Given the following DOM structure:
```
<header class="container mw-100">
  <div class="row h-100">
    <div class="col">
      <h1>{{ title }}</h1>
      <p>{{ testvar }}</p>
    </div>
  </div>
</header>
<main class="container mw-100">
  <section class="row">
    <nav class="col-2">
      <p>
        Nav
      </p>
    </nav>
    <article class="col-8">
      <p>
        Article
      </p>
    </article>
    <aside class="col-2">
      <p>
        Aside
      </p>
    </aside>
  </section>
</main>
<footer class="container mw-100">
  <div class="row h-100">
    <div class="col">
      <p>
        Footer
      </p>
    </div>
  </div>
</footer>
```

![angularbootstraplayout](https://raw.githubusercontent.com/kesselaprod/angularbootstrapheightcsslayout/master/images/angular_bootstrap_layout.png)

Now we define the height and position of our elements to form a classic **header - content (main > section > nav, article, aside) - footer** html 5 layout without a wrapper. The special feature here is the **footer** will always stick to the bottom and the **article column** will fill the remaining height regardless of the content or screen size. For this to happen we need to give the **header** and **footer** a fixed height and subtract the total pixel size from the proper value (```100vh/100%```). We also need to make sure our **footer** has a ```position: relative;``` and our **main** and **article** have both definitions for ```min-height``` (plus an additional ```height``` definition for **article** to fit the content size.)

Don't mind the interpolation placeholders ```{{ title }} {{ testvar }}``` they are only necessary if you are interested in angular app development.

This is what our corresponding **style.css** looks like:
```
html, body {
    height: 100%;
}

header {
    height: 100px;
}

main {
    min-height: calc(100% - 250px);
}


article {
    height: calc(100% - 250px);
    min-height: calc(100vh - 250px);
}

footer {
    height: 150px;
    position:relative; 
    bottom:0;
}
```
![angularbootstraplayoutextended1](https://github.com/kesselaprod/angularbootstrapheightcsslayout/blob/master/images/angular_bootstrap_layout_extended_1.png?raw=true)

![angularbootstraplayoutextended2](https://github.com/kesselaprod/angularbootstrapheightcsslayout/blob/master/images/angular_bootstrap_layout_extended_2.png?raw=true)
