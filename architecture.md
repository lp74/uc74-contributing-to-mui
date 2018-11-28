[contributing](contributing.md)

---

# Architecture

> To be defined

```
  /dist (here goes the build)
    img/
      ..
    fonts/
      ..
    mui.core.css (stylesheet) <= CSS can be used without a framework
    mui.js (utilities) <= Vanilla js
  /front-end-2
    /ui-layout
      /core/cux
        /fonts
        /style
          ...
          _breackpoints.less
          _font-faces.less
          ...
          _utilities.less
          _variables.less
          layout.less (import core ui-components)
        /..
    /ui-components
      /core/cux (i.e. buttons, inputs, tabs, navigator)
        /component-nane
        /components-group
          /component-name
        /notifications
          /message
            message.directive.js
            message.html
            message.less
            message.spec.js
            readme.md
            /doc
              html.md
              javascript.md
      /opt/cux
        ... (i.e. gauges, charts ...)
    /ui-composites
      /cux
  
  /app
    /www
      /bower_components
      /ui-components
      /ui-composites
      /connectivity
      /dashboard
        dashboard.controller.js (module: app.dashboard)
        dashboard.html
        ..
      /login
        login.controller.js (module: app.login)
        login.html
      /status-summary
      /style
        app.less (only application classes)
        mui.opt.less (imported from mui optional ui-components ad other ui-composites)
      /services
      /sessions
      /...
    /...
    ...
```

---

[contributing](contributing.md)