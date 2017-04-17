# Internationalization

The internationalization module provides some features to handle string resources, throw the right locale.

## Managing resources

### Loader

### Resource

## Locale

The locale is defined by a country and a language. A language alone, is not enough. Indeed, somes languages, as French are different, regarding to the country which use it.

By default, the locale used is **en\_US.**

### Country

The list of countries available is the following:

* France: "FR"
* USA: "US"

A new country can also be added:

```cpp
static const Country USA = "US";
```

### Language

The list of languages available is the following:

* French: "fr"
* English: "en"

A new language can also be added:

```cpp
static const Language ENGLISH = "en";
```

## File

## Example

```cpp
#include <iostream>
#include "Locale\ResourceLoader.hpp"
#include "Locale\Country.hpp"
#include "Locale\Language.hpp"

auto main() -> int
{
    ece::ResourceLoader::setPath("../examples/Internationalization/");

    ece::ResourceLoader loader("test");
    auto & resource = loader.getResource();
    std::cout << "########## Default Locale en_US ##########" << std::endl;
    std::cout << resource["helloworld"] << std::endl;
    std::cout << resource["example"] << std::endl;

    std::cout << std::endl;

    loader.changeLocale(ece::Locale(ece::FRENCH, ece::FRANCE));
    std::cout << "########## Locale fr_FR ##########" << std::endl;
    std::cout << resource["helloworld"] << std::endl;
    std::cout << resource["example"] << std::endl;

    return EXIT_SUCCESS;
}
```

This example is available on the [Github repository of the project](https://github.com/Isilin/Edencraft "Github repository of the project").

