Data Cube UI
=================

The work on Data Cube UI was inspired from [**CEOS Data Cube UI**](https://github.com/ceos-seo/data_cube_ui). The CEOS Data Cube UI is a full stack Python web application used to perform analysis on raster datasets using the Data Cube. Using common and widely accepted frameworks and libraries, our UI is a good tool for demonstrating the Data Cube capabilities and some possible applications and architectures. 

Landsat 8 data available in the S3 storage was used for our analysis. For indexing the Landsat 8, follow the [**indexing documentation**](https://datacube-core.readthedocs.io/en/latest/ops/indexing.html). The CEOS Data Cube UI was not functional for the Landsat 8 data we indexed, throwing errors related to chunking of data as well as improper rendering of result on the UI map as a result of the GDAL 3.x libraries used in our setup. This setup of the CEOS Data Cube UI resolves these erros and returns back the intented output.

Note - Custom mosaic tool is functional now. Others can be modified similarly to make them functional.

The UI's core technologies are:
* [**Django**](https://www.djangoproject.com/): Web framework, ORM, template processor, entire MVC stack
* [**Celery + Redis**](http://www.celeryproject.org/): Asynchronous task processing
* [**Data Cube**](http://datacube-core.readthedocs.io/en/stable/): API for data access and analysis
* [**PostgreSQL**](https://www.postgresql.org/): Database backend for both the Data Cube and our UI
* [**Apache/Mod WSGI**](https://en.wikipedia.org/wiki/Mod_wsgi): Standard service based application running our Django application while still providing hosting for static files
* [**Bootstrap3**](http://getbootstrap.com/): Simple, standard, and easy front end styling

Using these common technologies provides a good starting platform for users who want to develop Data Cube applications. Using Celery allows for simple distributed task processing while still being performant. Our UI is designed for high level use of the Data Cube and allow users to:
* Access various datasets that we have ingested
* Run custom analysis cases over user defined areas and time ranges
* Generate both visual (image) and data products (GeoTiff/NetCDF)
* Provide easy access to metadata and previously run analysis cases

Requirements
=================

* Full Data Cube installation with ingested data

* apache2
* libapache2-mod-wsgi-py3
* redis-server
* libfreeimage3
* tmux
* django
* redis
* celery
* imageio
* django-bootstrap3
* matplotlib
* stringcase

For more detailed instructions, please read the [documentation](docs/ui_install.md). If you want to add a new algorithm to the UI, you can follow our [adding a new algorithm](docs/adding_new_pages.md) documentation.