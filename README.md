# TTRC - Tierpsy Tracker Result Comprobation

**Process Description:**

A Python script was developed to verify the presence of data within a set of files with the `.hdf5` extension. The primary objective was to confirm whether these files contain datasets (arrays of data) and, if so, to provide basic information about their structure.

The script performs the following actions for each provided `.hdf5` file:

* **Mount Google Drive:** The `drive.mount('/content/drive')` function is used to access files stored in the user's Google Drive account within the Google Colaboratory environment.
* **Iterate over the list of files:** A list (`file_names`) is defined, containing the paths of the `.hdf5` files to be analyzed. The script then iterates over each file name in this list.
* **Open the HDF5 file:** For each file, an attempt is made to open it in read mode (`'r'`) using the `h5py` library. This allows inspection of its contents without modification.
* **Print the file structure:** The `hdfid.visit()` function, along with a local function (`print_name`), is used to traverse all elements within the HDF5 file (both datasets and groups) and display its hierarchical structure.
* **Verify and display dataset information:** The top-level keys of the file are iterated over. If a key corresponds to a dataset (`h5py.Dataset`), the script extracts and prints the following information:
    * The name of the dataset.
    * Its shape (dimensions) using `.shape`.
    * The data type stored using `.dtype`.
    * The total number of elements using `.size`.
    * **Exemplification:** For datasets with up to two dimensions and a size smaller than 100 elements, the first 5 rows of the data are printed as an example of their content. For larger datasets, it is indicated that they are too large to print completely.
* **Identify groups:** If a key corresponds to a group (`h5py.Group`), it is indicated as a group.
* **Handle files without datasets:** Logic is included to identify and report files that do not contain top-level datasets.
* **Error handling:** `try...except` blocks are used to handle potential errors such as files not found (`FileNotFoundError`) or other errors that may occur while opening or reading the files.


This script enables an efficient check of the presence and basic structure of the data contained in multiple `.hdf5` files. By printing the structure and key information of the datasets (shape, data type, and size), it can be verified whether the files contain the expected information. Printing the first few rows of small datasets serves as an exemplification of the stored data type.
