# README

Demo of hugo build error.

Just build with 
```bash
hugo --gc --cleanDestinationDir --ignoreCache --logLevel debug
```

(Hugo version 0.145.0 extended)

If I try to build with the latest release from github, I get this error:

```
$ hugo --gc --cleanDestinationDir --ignoreCache --logLevel debug
INFO  deprecated: the ":slugorfilename" permalink token was deprecated in Hugo 0.144.0 and will be removed in a future release. Use ":slugorcontentbasename" instead.
INFO  deprecated: the ":slugorfilename" permalink token was deprecated in Hugo 0.144.0 and will be removed in a future release. Use ":slugorcontentbasename" instead.
INFO  deprecated: the ":slugorfilename" permalink token was deprecated in Hugo 0.144.0 and will be removed in a future release. Use ":slugorcontentbasename" instead.
Start building sites … 
hugo v0.145.0-666444f0a52132f9fec9f71cf25b441cc6a4f355+extended linux/amd64 BuildDate=2025-02-26T15:41:25Z VendorInfo=gohugoio

INFO  static: removing all files from destination that don't exist in static dirs
INFO  static: syncing static files to / duration 2.668456ms
INFO  build:  step process substep collect files 10 files_total 10 pages_total 10 resources_total 0 duration 1.319876ms
INFO  build:  step process duration 1.377254ms
DEBUG Set expanded permalink path for page pages/about.md to "/about/"
DEBUG Set expanded permalink path for page pages/free_trial.md to "/free_trial/"
DEBUG Set expanded permalink path for page pages/pricing.md to "/pricing/"
DEBUG Set expanded permalink path for page pages/see_a_demo.md to "/see_a_demo/"
INFO  build:  step assemble duration 784.602µs
ERROR render of "/home/myuser/projects/hugo_error_example/content/_index.md" failed: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/_default/baseof.html:22:7": execute of template failed: template: index.html:22:7: executing "index.html" at <partialCached "essentials/style.html" .>: error calling partialCached: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/partials/essentials/style.html:47:33": execute of template failed: template: partials/essentials/style.html:47:33: executing "partials/essentials/style.html" at <resources.Concat>: error calling Concat: resources in Concat must be of the same Media Type, got "text/x-scss" and "text/css"
ERROR render of "/home/myuser/projects/hugo_error_example/content/legal/claims.md" failed: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/_default/baseof.html:22:7": execute of template failed: template: _default/single.html:22:7: executing "_default/single.html" at <partialCached "essentials/style.html" .>: error calling partialCached: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/partials/essentials/style.html:47:33": execute of template failed: template: partials/essentials/style.html:47:33: executing "partials/essentials/style.html" at <resources.Concat>: error calling Concat: resources in Concat must be of the same Media Type, got "text/x-scss" and "text/css"
ERROR render of "/404" failed: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/_default/baseof.html:22:7": execute of template failed: template: 404.html:22:7: executing "404.html" at <partialCached "essentials/style.html" .>: error calling partialCached: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/partials/essentials/style.html:47:33": execute of template failed: template: partials/essentials/style.html:47:33: executing "partials/essentials/style.html" at <resources.Concat>: error calling Concat: resources in Concat must be of the same Media Type, got "text/x-scss" and "text/css"
ERROR render of "/home/myuser/projects/hugo_error_example/content/legal/privacy.md" failed: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/_default/baseof.html:22:7": execute of template failed: template: _default/single.html:22:7: executing "_default/single.html" at <partialCached "essentials/style.html" .>: error calling partialCached: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/partials/essentials/style.html:47:33": execute of template failed: template: partials/essentials/style.html:47:33: executing "partials/essentials/style.html" at <resources.Concat>: error calling Concat: resources in Concat must be of the same Media Type, got "text/x-scss" and "text/css"
INFO  build:  step render pages 17 content 13 duration 32.882889ms
INFO  build:  step render deferred count 0 duration 431ns
INFO  build:  step postProcess duration 8.607µs
ERROR TOCSS: failed to transform "style.scss" (text/x-scss): resource "scss/style.scss_d9077b5cab49df084fb1a39ad4b1e75d" not found in file cache
INFO  build:  duration 35.224833ms
Total in 70 ms
Error: error building site: render: failed to render pages: render of "/home/myuser/projects/hugo_error_example/content/pages/free_trial.md" failed: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/_default/baseof.html:22:7": execute of template failed: template: _default/single.html:22:7: executing "_default/single.html" at <partialCached "essentials/style.html" .>: error calling partialCached: "/home/myuser/projects/hugo_error_example/themes/andromeda-light-hugo/layouts/partials/essentials/style.html:47:33": execute of template failed: template: partials/essentials/style.html:47:33: executing "partials/essentials/style.html" at <resources.Concat>: error calling Concat: resources in Concat must be of the same Media Type, got "text/x-scss" and "text/css"
```

It seems that the root error is `ERROR TOCSS: failed to transform "style.scss" (text/x-scss): resource "scss/style.scss_d9077b5cab49df084fb1a39ad4b1e75d" not found in file cache`. I've searched the discussions and there are similar discussions, but they seem to resolve by using the extended version. However, I am using the extended version.
