# Internationalization

The internationalization module provides some features to handle string resources, according to the right locale.

## Managing resources

A container is available to load a resource file and to get the string resources.

### Loader

Before loading a resource file, it is required to set up the root path:

```cpp
ece::ResourceLoader::setPath("../examples/Internationalization/");
```

Then, it is only needed to use the name of the resource file whished. The name of the file will be completed, according to the locale defined in the loader.

### Resource

Once, a resource has been loaded, throw the loader, a string resource can be accessed, obviously, using the mapping mechanism:

```cpp
std::cout << resource["example"] << std::endl;
```

## Locale

The locale is defined by a country and a language. A language alone, is not enough. Indeed, some languages, as French are different, regarding to the country which use it.

By default, the locale used is **en\_US.**

### Country

The list of countries available is the following:

* France: "FR"
* USA: "US"

A new country can also be added:

```cpp
static const ece::Country USA = "US";
```

### Language

The list of languages available is the following:

* French: "fr"
* English: "en"

A new language can also be added:

```cpp
static const ece::Language ENGLISH = "en";
```

## File

A file resource can be created has a valid JSON file with one depth level. It has to be named following a specific pattern:

```
<name>_<language>_<country>.json
```

Each new entry of the resource, is composed of a key and a value. The key should be unique in all the file, and the same in each locale file. The value could be anything as a string format.

###### test\_en\_US.json

```js
{
    "helloworld": "Hello World!",
    "example": "This line is a wonderful example of the module internationalization working ..."
}
```

###### test\_fr\_FR.json

```js
{
    "helloworld": "Bonjour tout le monde",
    "example": "Cette ligne est un incroyable example de mon module internationalisation en fontionnement ..."
}
```

## Example

###### Example.cpp

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

