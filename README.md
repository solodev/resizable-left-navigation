# resizable-left-navigation
Your sidebar or left navigation may have content that needs to expand past the default width. One way to account for this is to make the left navigation resizable, thus allowing users to expand and collapse it by dragging.  

## Tutorial
For detailed instruction's, view Solodev's [How to Create a Resizable Left Navigation](http://www.solodev.com/blog/web-design/how-to-create-a-resizable-left-navigation.stml)

## Demo
Try out a working example on [JSFiddle](https://jsfiddle.net/solodev/r8nghust/).

## HTML
The tutorial contains the following basic HTML markup.

```
 <body>

   <div class="wrapper">
     <aside id="resizable" class="sidebar-left movable-div position-fixed bottom-0 left-0 animated">
       <div class="sidebar-logo position-relative pt-3">
         <a href="#" class="logo">
           <img src="https://github.com/solodev/resizable-left-navigation/blob/master/images/logo.png?raw=true" alt="Logo" class="img-fluid p-4">
         </a>
       </div>
       <hr />
       <div class="nano has-scrollbar">
         <nav class="nano-content" tabindex="0" style="right: -17px;">
           <ul class="nav nav-main">
             <li id="dashboard-nav" class="p-0 w-100">
               <div class="sidebar-sticky">
                 <h5 class="sidebar-heading d-flex justify-content-between align-items-center px-3 mt-4 mb-1 text-muted">
                   <span>Locations</span>
                 </h5>
                 <ul class="flex-column">
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       XP-1
                     </a>
                   </li>
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       HAB-1
                     </a>
                   </li>
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       Orbiter-1
                     </a>
                   </li>

                 </ul>

                 <h5 class="sidebar-heading d-flex justify-content-between align-items-center px-3 mt-4 mb-1 text-muted">
                   <span>Products</span>
                 </h5>
                 <ul class="flex-column">
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       VALKYRIE-1
                     </a>
                   </li>
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       TALON-2
                     </a>
                   </li>
                   <li class="nav-item">
                     <a class="nav-link" href="#">
                       <i class="fa fa-file-text-o" aria-hidden="true"></i>
                       LUNAR XPLORER
                     </a>
                   </li>
                 </ul>
               </div>
             </li>
           </ul>
         </nav>
         <div class="nano-pane" style="display: none;">
           <div class="nano-slider" style="height: 1246px; transform: translate(0px, 0px);"></div>
         </div>
       </div>
       <div class="draghandle" style="width: 6px; height: 100vh;"></div>
     </aside>
     <div id="mainArea" class="content marginLeft d-flex h-100 flex-column">
       <article class="col-lg-8 content-page--text">
         <div class="row">
           <div class="col-12 col-centered">
             <h1 class="text-center p-5">The Cosmos Awaits</h1>
             <p class="mb-4">Rogue cosmos muse about Rig Veda concept of the number one hydrogen atoms.
               Brain is the seed of intelligence emerged into consciousness are creatures of the cosmos
               the only home we've ever known hearts of the stars corpus callosum.
               Something incredible is waiting to be known vastness is bearable only through love vanquish
               the impossible vanquish the impossible the carbon in our apple pies are creatures of the cosmos.</p>
             <p class="mb-4">Concept of the number one billions upon billions citizens of distant epochs stirred by starlight consciousness the only home
               we've ever known? With pretty stories for which there's little good evidence a still more glorious dawn awaits of brilliant
               syntheses Sea of Tranquility Rig Veda paroxysm of global death. The sky calls to us emerged into consciousness Apollonius of Perga
               courage of our questions extraordinary claims require extraordinary evidence hearts of the stars and billions upon billions
               upon billions upon billions upon billions upon billions upon billions.</p>
           </div>
         </div>
       </article>
     </div>
   </div>
 </body>
```

## JS
```

$(document).ready(function() {
        var element = document.getElementById('resizable');
        if (element) {
          var resizer = document.createElement('div');
          resizer.className = 'draghandle';
          resizer.style.width = '6px';
          resizer.style.height = '100vh';
          element.appendChild(resizer);
          resizer.addEventListener('mousedown', initResize, false);
        }

        function initResize(e) {
          window.addEventListener('mousemove', Resize, false);
          window.addEventListener('mouseup', stopResize, false);
          $('#mainArea.content, #tabs iframe').addClass('marginLeft');
        }

        function Resize(e) {
          element.style.width = (e.clientX - element.offsetLeft) + 'px';
          $('#mainArea.content').css('margin-left', (e.clientX - element.offsetLeft) + 'px');
          $('#tabs iframe').css('margin-left', (element.offsetLeft + 40) + 'px');
        }

        function stopResize(e) {
          window.removeEventListener('mousemove', Resize, false);
          window.removeEventListener('mouseup', stopResize, false);
          $('#tabs iframe').css('margin-left', element.offsetLeft + 'px');
        }
      });
```

## CSS
All required CSS is contained with style.css

## External Resources
This tutorial includes the following third party resources.

```
<!-- Bootstrap CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
<!-- FontAwesome CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.css">
<!-- jQuery first, then Popper.js, then Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
```