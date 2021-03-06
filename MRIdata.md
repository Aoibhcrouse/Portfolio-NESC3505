<style>
  h1{color:Purple !important;}
  h2{color:Grey !important;}
</style>
<div>
    <h1>MRI Data Visualiztion</h1>
</div>
<br />
<div>
    <h2>Import Packages</h2>
    <p>This shows all of the python packages and their respective aliases needed to work with our data</p>
</div>
```python
import imageio as iio
import scipy.ndimage as ndi
import scipy.stats
import nibabel as nib
import numpy as np
import matplotlib.pyplot as plt
```
<div>
    <h2>Read in Data</h2>
    <p>This shows how to read in DICOM files using the imageio package and how to show some characteristics about our data.</p>
</div>
```python
brain_img = iio.imread('data/IM-0004-0096.dcm')
```
<div>
    <p>This shows the metadata of our data.</p>
</div>
```python
brain_img.meta
```




    Dict([('TransferSyntaxUID', '1.2.840.10008.1.2.1'),
          ('SOPClassUID', '1.2.840.10008.5.1.4.1.1.4'),
          ('SOPInstanceUID',
           '1.2.840.113619.2.176.3596.7771172.7255.1265293350.477'),
          ('StudyDate', '20100204'),
          ('SeriesDate', '20100204'),
          ('AcquisitionDate', '20100204'),
          ('ContentDate', '20100204'),
          ('StudyTime', '201859'),
          ('SeriesTime', '202511'),
          ('AcquisitionTime', '202511'),
          ('ContentTime', '202511'),
          ('Modality', 'MR'),
          ('Manufacturer', 'GE MEDICAL SYSTEMS'),
          ('InstitutionName', 'IWK Health Centre'),
          ('SeriesDescription', 'SAG 3D T1 SPGR'),
          ('PatientName', 'AARONTEST'),
          ('PatientID', 'AARONTEST'),
          ('PatientBirthDate', ''),
          ('PatientSex', 'M '),
          ('PatientAge', '000Y'),
          ('PatientWeight', 70.307),
          ('SliceSpacing', 1.0),
          ('StudyInstanceUID',
           '1.2.840.113619.2.176.3596.7771172.7628.1265291937.899'),
          ('SeriesInstanceUID',
           '1.2.840.113619.2.176.3596.7771172.7628.1265291937.902'),
          ('SeriesNumber', 4),
          ('AcquisitionNumber', 1),
          ('InstanceNumber', 96),
          ('ImagePositionPatient', (-1.60062, -178.036, 97.0647)),
          ('ImageOrientationPatient', (-0.0, 1.0, 0.0, -0.0, -0.0, -1.0)),
          ('SamplesPerPixel', 1),
          ('Rows', 256),
          ('Columns', 256),
          ('PixelSpacing', (1.0, 1.0)),
          ('BitsAllocated', 16),
          ('BitsStored', 16),
          ('HighBit', 15),
          ('PixelRepresentation', 1),
          ('PixelData',
           b'Data converted to numpy array, raw data removed to preserve memory'),
          ('shape', (256, 256)),
          ('sampling', (1.0, 1.0))])


<div>
    <p>This shows the dimensions of our images in the data.</p>
</div>
```python
brain_img.shape
```




    (256, 256)
<div>
    <h2>View Images</h2>
    <p>This shows how to view a single MRI image when there is only one in the data.</p>
</div>

```python
plt.imshow(brain_img, cmap = 'bone')
plt.axis('off')
plt.show()
```


<img src="mri1.png" width="650px" />    


<div>
    <h2>New Data</h2>
    <p>This is reading in more MRI data to work with. The output is a little scary, it is just saying what image is being uploaded and what percentage is uploaded.</p>
</div>

```python
vol = iio.volread('data/SAG3DT1SPGR_4')
```

    Reading DICOM (examining files): 1/184 files (0.5%)3/184 files (1.6%)5/184 files (2.7%)9/184 files (4.9%)13/184 files (7.1%)17/184 files (9.2%)19/184 files (10.3%)22/184 files (12.0%)25/184 files (13.6%)29/184 files (15.8%)32/184 files (17.4%)35/184 files (19.0%)38/184 files (20.7%)41/184 files (22.3%)46/184 files (25.0%)48/184 files (26.1%)55/184 files (29.9%)63/184 files (34.2%)73/184 files (39.7%)78/184 files (42.4%)88/184 files (47.8%)94/184 files (51.1%)100/184 files (54.3%)102/184 files (55.4%)104/184 files (56.5%)111/184 files (60.3%)115/184 files (62.5%)117/184 files (63.6%)125/184 files (67.9%)128/184 files (69.6%)136/184 files (73.9%)140/184 files (76.1%)144/184 files (78.3%)151/184 files (82.1%)158/184 files (85.9%)169/184 files (91.8%)183/184 files (99.5%)184/184 files (100.0%)
      Found 1 correct series.
    Reading DICOM (loading data): 184/184  (100.0%)
<br />
<div>
    <p>This gets the dimensions of the data that was just read in.</p>
</div>

```python
vol.shape
```



    (184, 256, 256)
<br />
<div>
    <p>This demonstrates how to view an MRI image when there are more than one in the data.</p>
</div>

```python
plt.imshow(vol[92], cmap = 'gray')
plt.axis('off')
plt.show()
```




    
<img src="Mri2.png" width="650px" />

<div>
    <p>This code is a variation of the one above; showing how to view multiple MRI images at once, showing every tenth image in the MRI series.</p>
</div>


```python
fig, axs = plt.subplots(4, 4, figsize=[8, 8])
start = int((vol.shape[0] - 160) / 2 )
stop = int(vol.shape[0] - start)

step_size = int((stop - start)/16)

for idx, img in enumerate(range(start, stop, step_size)):
    axs.flat[idx].imshow(vol[img, :, :], cmap='gray')
    axs.flat[idx].axis('off')
        
plt.tight_layout()
plt.show()
```




    
<img src="MultiMri.png" width="650px" />

<div>
    <p>This code shows a cool vairation of the classic sagittal sections shown in MRI, using this code, we make it so that we see a horizontal section.</p>
</div>


```python
id = vol[:, :, 92]
plt.imshow(id, cmap = 'gray')
plt.show()
```




    
<img src="HorizontalMri.png" width="650px" />    

<div>
    <p>The last image is a little difficult to make much sense of, rotating the image by 90 degrees makes it much easier to see what is going on.</p>
</div>


```python
id = vol[:, :, 92]
plt.imshow(ndi.rotate(id, 270), cmap = 'gray')
plt.show()
```




    
<img src="90horizontalMri.png" width="650px" />    

<div>
    <h2>Read in fMRI Data</h2>
    <p>The imageio package that we have been using to view the MRI data does not work with fMRI data, so we need to use the NiBabel package to read in the fMRI data.</p>
</div>

```python
brain_vol = nib.load('data/language_zstat1.nii.gz')
```
<div>
    <p>This shows the metadata about the fMRI image data.</p>
</div>

```python
print(brain_vol.header)
```

    <class 'nibabel.nifti1.Nifti1Header'> object, endian='<'
    sizeof_hdr      : 348
    data_type       : b''
    db_name         : b''
    extents         : 0
    session_error   : 0
    regular         : b'r'
    dim_info        : 0
    dim             : [  3  91 109  91   1   1   1   1]
    intent_p1       : 0.0
    intent_p2       : 0.0
    intent_p3       : 0.0
    intent_code     : z score
    datatype        : float32
    bitpix          : 32
    slice_start     : 0
    pixdim          : [-1.  2.  2.  2.  1.  0.  0.  0.]
    vox_offset      : 0.0
    scl_slope       : nan
    scl_inter       : nan
    slice_end       : 0
    slice_code      : unknown
    xyzt_units      : 10
    cal_max         : 0.0
    cal_min         : 0.0
    slice_duration  : 0.0
    toffset         : 0.0
    glmax           : 0
    glmin           : 0
    descrip         : b'FSL5.0'
    aux_file        : b''
    qform_code      : mni
    sform_code      : mni
    quatern_b       : 0.0
    quatern_c       : 1.0
    quatern_d       : 0.0
    qoffset_x       : 90.0
    qoffset_y       : -126.0
    qoffset_z       : -72.0
    srow_x          : [-2.  0.  0. 90.]
    srow_y          : [   0.    2.    0. -126.]
    srow_z          : [  0.   0.   2. -72.]
    intent_name     : b''
    magic           : b'n+1'

<div>
    <p>This is how to extract the data and store it as an array, the output is just making sure that it makes an array.</p>
</div>

```python
fmri_zstat_data = brain_vol.get_fdata()

type(fmri_zstat_data)
```




    numpy.ndarray

<div>
    <p>The dimensions of the images.</p>
</div>


```python
fmri_zstat_data.shape
```




    (91, 109, 91)

<div>
    <p>This shows another series of images, but in the horizontal section and with fMRI images. It looks mottled due to intensity values, showing that the brain is organized into distinct functional regions.</p>
</div>


```python
fig, axs = plt.subplots(3, 3, figsize=[8, 8])

start = 20
stop  = 61
step = 5

step_size = int((stop - start)/8)

for idx, img in enumerate(range(start, stop, step_size)):
    axs.flat[idx].imshow(fmri_zstat_data[:, :, img], cmap='gray')
    axs.flat[idx].axis('off')

plt.tight_layout()
plt.show()
```




    
<img src="BlurryMri.png" width="650px" />    

<div>
    <p>This series of fMRI images shows different colors (red and blue) to represent different activations in the brain.</p>
</div>

```python
fig, axs = plt.subplots(3, 3, figsize=[8, 8])

start = 20
stop  = 61
step = 5

step_size = int((stop - start)/8)
fmrix = fmri_zstat_data.max()
fmrin = -abs(fmri_zstat_data.max())

for idx, img in enumerate(range(start, stop, step_size)):
    axs.flat[idx].imshow(fmri_zstat_data[:, :, img], vmax=fmrix, vmin=float(fmrin),cmap='seismic')
    axs.flat[idx].axis('off')

plt.tight_layout()
plt.show()
```




    
<img src="ColorMri.png" width="650px" />    


