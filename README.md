RCVS
====

Module for automatization of geo-processing workflow over raster and vector data.
————————————————————————————————————

**About**

Inspired by/based on `RIOS` module for *Raster Computer Vision Simplification*.

*credits*:      `grazzja <jacopo.grazzini@ec.europa.eu>`_ 

*version*:      0.9

*since*:        Fri May 31 10:20:51 2013

**Description**
   
Python basic tools for geo-processing workflow of raster and vector data:
    - using the input/output utility functions of [RIOS][RIOS] (Raster Input Output
      Simplification) module, itself based on |gdal| module,
    - using external Computer Vision and Image Processing processing (CVIP) 
      algorithms provided (when installed independently) by modules like |PIL|, 
      |OpenCV|, |skimage|, |matplotlib| and/or |scipimage|\ .

This way, a 'simple' definition of processing workflow is possible
                
**Note**

Only the :meth:`applier` (block) processor has been override: this functionality is 
available (in the original code) through the `apply` function of the module 
`applier.py`\ . This function has been rewritten (and improved) in overriding
`rcvs.cvapplier` method. 

The main features of the new `rcvs.cvapplier` method are:
    - apply a workflow of CVIP methods over the raster images through 
      appropriate redirection/reformatting of input/output block of data as it 
      deals with all the array format conversions necessary for 'communication' 
      between the different CVIP modules used,
    - process blocks in parallel through a map/reduce (namely: apply_async`/`reduce`) 
      like schema as it supports block and CPU multiprocessing,
    - return or write multiple outputs.
    
Note that from version 1.2, parallel implementation has also been incorporated 
(using either `multiprocessing` or `mpi` module) in |RIOS|.

**Examples**
                
As to demonstrate how to reproduce some of the standard/simple CVIP processing
workflows, some examples provided by CVIP platforms have been adapted using 
RCVS, namely:
    - RANSAC matching with |skimage| methods, 
    - SLIC segmentation with |skimage| methods,
    - pyramid decomposition with |OpenCV| methods, 
    - template matching with |OpenCV| methods, 

as well as some independent implementations:
    - image cross-correlation.

**Dependencies**

*require*:      `gdal`, `rios`, `numpy`, `scipy`,       \
                `Queue`, `multiprocessing`,                       \
                `math`, `re`, `inspect`, `operator`,    \    
                `itertools`, `collections`           

*optional*:     `cv2`, `skimage`, `PIL`, `matplotlib`,  \
                `vigra`, `mahotas`
                pathos

.. Links

[RIOS]: https://bitbucket.org/chchrsc/rios
_gdal: https://github.com/geopy/geopy
|gdal| replace:: `gdal <gdal_>`_
_matplotlib: http://matplotlib.org
|matplotlib| replace:: `matplotlib <matplotlib_>`_
_OpenCV: http://opencv.org
|OpenCV| replace:: `OpenCV <OpenCV_>`_
_skimage: http://scikits.appspot.com/scikits-image
|skimage| replace:: `skimage <skimage_>`_
_PIL: http://www.pythonware.com/products/pil
|PIL| replace:: `PIL <PIL_>`_
_vigra: http://ukoethe.github.io/vigra/doc/vigranumpy/index.html
|vigra| replace:: `vigra <vigra_>`_
_mahotas: http://luispedro.org/software/mahotas
|mahotas| replace:: `mahotas <mahotas_>`_
_scipimage : http://docs.scipy.org/doc/scipy/reference/ndimage.html
|scipimage| replace:: `scipy.ndimage <scipimage_>`_