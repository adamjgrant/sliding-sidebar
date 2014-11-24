sliding-sidebar
===============

Full page sliding sidebar component for Kickstart

This component requires the use of four mixins:
- `clip()`
- `clip-canvas()`
- `clip-main()`
- `clip-aside()`

# Clip

The clip is the full width box that will contain everything--your sidebar and 
the main page content. Its purpose is to clip off any internal content that 
bleeds out of the viewport.

This element should be placed very high in the DOM

    <html>
      ...
      <body>
        <div class="clip">

        </div>
      </body>
    </html>

    .clip { @include clip(); }

The clip mixin is where you'll define any customizations, like sidebar width:

    .clip { @include clip(300px); }

# Canvas

Inside the clip, you'll need to add the full canvas (The container that moves
left and right).

    <html>
      ...
      <body>
        <div class="clip">
          <section>
            <main></main>
            <aside></aside>
          </section>
        </div>
      </body>
    </html>

    .clip { @include clip(); }

`section` must be a direct descendant of `.clip` and it must have the direct
descendants `main` and `aside`.

`main` will be where your page's content goes. `aside` will hold your sidebar
content.

# Open and Closing sidebar

To open or close, simply toggle the `open` class on `section`.

    <!-- Open -->
    <div class="clip">
      <section class="open">

    <!-- Closed -->
    <div class="clip">
      <section>

Here's how to do this with a helper included in kickstart.js

    // Open
    k$.$('.clip section').classList.add('open');

    // Open
    k$.$('.clip section').classList.remove('open');
