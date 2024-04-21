# HPC Data Processing

- Contains all notebooks needed to process NavCan images into train/test/validation datasets on ECCC HPC.
- The paths in the notebooks are hard-coded to be ran for `hol002` (Hokyung Lee) account. Please adjust the paths or values in the notebooks accordingly when running it on your HPC account.
- Note, the data processing code for processing 5 additional NavCan webcams are currently in-progress.
- Run the notebooks in-order.

### METAR Docs Processing Notebooks

> 1. webcam_extract_wxcodes_text.ipynb

- Reads the `<PROVINCAL_CODE>_ASOS.csv` METAR files and classifies each item into one of 7 precip types using the wxcode. Outputs `<PROVINCAL_CODE>_ASOS_Precipitation.csv` METAR files.

> 2. webcam_sample_dataset_report_matching.ipynb

- Reads the `<PROVINCAL_CODE>_ASOS_Precipitation.csv` METAR files and matches each row to an image based on the location and time. Outputs `<PROVINCIAL_CODE>_ASOS_Matched.csv` METAR files.

### 37 NavCan Webcams Processing Notebooks

> 3. webcam_sample_dataset_extraction.ipynb

- Takes the raw .tgz files located at `/space/hall5/sitestore/eccc/mrd/rpnarmp/snow000/NavCan_WxCams/` and converts them into directories of images at your ECCC HPC account folder for further data processing.

> 4. webcam_sample_dataset_preprocessing_complete.ipynb

- For each unzipped directories of images, this notebook crops the images into specific dimension (e.g. 224px by 224px), filters out images that are invalid or too dark, and classify the images to each precip type (currently set to No Precip vs Rain vs Snow vs Ice).

> 5. reduced_class_dataset_preprocessing.ipynb

- Creates new directories for train/test/validation datasets, then for No Precip vs Rain vs Snow precip types, (1) moves 1K images to each test/validation datasets, and (2) copies rest of the images over-and-over to a set number of images (94K) to balance the training dataset.
- Used to create the [reduced_class_images](https://drive.google.com/drive/folders/1GCvFJ6ssquHjsYZmMDBlpvBUe8c3wurk?usp=drive_link) dataset.

> reduced_class_with_ice_dataset_preprocessing.ipynb

- Same as `reduced_class_dataset_preprocessing.ipynb`, except for No Precip vs Rain vs Snow vs Ice precip types.
- Used to create the [reduced_class_with_ice_images](https://drive.google.com/drive/folders/1erpQh78KzOcGgV-hwj9XJtr5wvBfV8wV?usp=drive_link) dataset.

> balanced_dataset_preprocessing.ipynb

- (not used anymore)
- Creates new directories for train/test/validation datasets, then for each precip types, (1) moves certain number of images to test/validation datasets, and (2) copies rest of the images over-and-over to a set number of images (10K) to balance the training dataset.
- Used to create the [balanced_70k_images](https://drive.google.com/drive/folders/1Oj1s3JuLldRMPaC3X7KPHoTIeu_DZ9cQ?usp=drive_link) dataset.

### 5 Additional NavCan Webcams Processing Notebooks

> 6. webcam_sample_dataset_extraction_additional_cameras_non_cyvr.ipynb

- Unzips .tgz files from `/space/hall5/sitestore/eccc/mrd/rpnarmp/snow000/` for `CYYZ`, `CYFB`, `CYXY`, and `CWSK`.

> 7. webcam_sample_dataset_extraction_from_urls.ipynb

- Downloads .tgz files via HTTP from `http://crispus.cmc.ec.gc.ca/~crawfordr/CETUS3/DATA2/cannow/archive/flexwatch/cyvr` for `CYVR`.

> Note

- Rest of the code hasn't been finished yet, please implement them similarly to the code for 37 NavCan webcams above.
