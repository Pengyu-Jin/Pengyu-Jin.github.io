## Popular Science
!!! question "Common abbreviations?"

    - After Est.Gas savings:After estimated gas savings
    - 396mi  range(EPA est.):续航里程为396英里，根据美国环境保护署EPA的估算。
    many knowledge you must learn

    === "abbreviations"

    mph: miles per hour

    mpg: miles per gallon(from fuel-economy standards)

    === "notes"
    
    1.99s  0-60mph:从0加速到60mph所用的时间仅为1.99s

    60mph=60miles/h=60*1.609=96.54km/h，与我们所说的百公里加速时间有一定误差

??? question "How to add plugins to the Docker image?"

    Material for MkDocs only bundles selected plugins in order to keep the size
    of the official image small. If the plugin you want to use is not included,
    you can add them easily:

    === "Material for MkDocs"

        Create a `Dockerfile` and extend the official image:

        ``` Dockerfile title="Dockerfile"
        FROM squidfunk/mkdocs-material
        RUN pip install mkdocs-macros-plugin
        RUN pip install mkdocs-glightbox
        ```

    === "Insiders"

        Clone or fork the Insiders repository, and create a file called
        `user-requirements.txt` in the root of the repository. Then, add the
        plugins that should be installed to the file, e.g.:

        ``` txt title="user-requirements.txt"
        mkdocs-macros-plugin
        mkdocs-glightbox
        ```

    Next, build the image with the following command:

## culture
gas-guzzler:  a car that uses a lot of petrol 高油耗汽车，油老虎

## vehicle kind
sport-utility vehicle (SUV)

pickup trucks

## brand
Volkswagen大众

Honda本田

Hyundai现代

Toyota丰田

Mitsubishi三菱

