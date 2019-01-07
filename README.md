# Holy Grail CSS Template

Provide grid and flexbox holy-grail layout. See the style tag for code.

## Example

_NB: See the style tag in the index file for details_

Given a layout like this:

```html
<body>
  <div id="main" class="app__layout">

    <header>
      <div class="header__logo">
        <h2>LOGO</h2>
      </div>
      
      <div class="header__title">
        <h1>Header</h1>
      </div>

      <nav class="header__nav">
        {...}
      </nav>
    </header>

    <main>
      <article class="main__content">
        {...}
      </article>
      <aside class="main__aside">
        {...}
      </aside>
    </main>

    <footer>
      {...}
    </footer>

  </div>
</body>
```

Outputs this:

![Holy grail layout](https://github.com/ajdelossantos/holy-grail-css-template/blob/master/holy-grail.png "Holy grail layout")

Implemented in grid with flexbox fallbacks.

```css
/*
\========================================
\ Flexbox
\========================================
*/

  .app__layout,
  header,
  main,
  footer {
    display: flex;
  }

  .app__layout{
    flex-direction: column;
  }

  header,
  main,
  footer {
    flex-direction: row;
  }

  .header__logo {
    flex: 1;
  }

  .header__title {
    flex: 2;
  }

  .header__nav {
    flex-direction: row;
    flex: 1;
    justify-content: center;
  }

  .main__content {
    flex: 3;
  }

  .main__aside {
    flex: 1;
  }

/*
\========================================
\ Grid
\========================================
*/

  .app__layout,
  header,
  main,
  footer {
    display: grid;
  }

  .app__layout {

    grid-template-areas:
    "header"
    "content"
    "footer";
  }

  header {
    grid-area: header;

    grid-template-areas:
    "logo title title nav"
  }

  .header__logo {
    grid-area: logo;
  }

  .header__title {
    grid-area: title;
  }

  .header__nav {
    grid-area: nav;
  }

  main {
    grid-area: content;

    grid-template-areas:
    "content content content aside"
  }

  .main__content {
    grid-area: content;
  }

  .main__aside {
    grid-area: aside;
  }

  footer {
    grid-area: footer;
  }
```

## Todo
- [ ] Implement responsive layout for mobile