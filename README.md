# CRM-TI (CRM Target Identifier)
CRM-TI: an enhanced pipeline for computationally assigning the target genes of
cis-regulatory modules by considering comprehensive long-range regulation mechanisms
Yu-Huai Yua, Guan-Liang Heb, Xing-Yo Wanga, Tzu-Hsien Yanga,c,∗

## Related paper:
Yu-Huai Yu+, Guan-Liang He+, Xing-Yo Wang, Tzu-Hsien Yang*, "CRM-TI: an enhanced pipeline for computationally assigning the target genes of cis-regulatory modules by considering comprehensive long-range regulation mechanisms", (submitting).

+: These authors contributed equally.

## Prepare the Environment

Suggested running environments: Linux Ubuntu 16.04.6, Python 3.8.13

We recommend that you can use the conda package to create a new environment. This will automatically install the required python packages. 

Here is an example: 

1. Install the Conda package for you system. The installation of the package can be found <a href="https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html">here</a>. 

2. Create the CRM-TI Conda environment. This may take a while, depending on the network status.

```
conda create -n "CRM-TI" python=3.8.13
```

3. Activate your CRM-TI Conda environment. 

```
conda activate CRM-TI
```

## Steps to Use CRM-TI

1. Download the codes from the following link and unzip the file. Please skip it if you have done this step.

```
wget https://cobis-fs.bme.ncku.edu.tw/CRM-TI/CRM-TI.tar.gz
```

2. Unzip the file.

```
tar -zxvf CRM-TI.tar.gz
```

3. Change the working directory.

```
cd CRM-TI
```

4. Download the processed epigenetic datasets from the following link.

```
wget https://cobis-fs.bme.ncku.edu.tw/CRM-TI/Data_dir.tar.gz
```

5. Unzip the file.

```
tar -zxvf Data_dir.tar.gz
```

6. If this is the first time you use CRM-TI, run the following command to install necessary packages. 

```
pip install -r requirements.txt
```

CRM-TI can also support GPU acceleration. If you want to utilize GPU, please run the following command instead:

```
pip install -r requirements_gpu.txt
```


7. Prepare the input Drosophila CRM regions (ver. dm6) and the genes of interest.
     
   (1) The input CRM format **SHOULD** followed the following formats:
   
   CRM\_[chromosome]\_[start]\_[end]
   
   (2) The input gene format **SHOULD** followed the following formats:
   
   [Gene name]\_[chromosome]\_[start]\_[end]@[Strand]
   
   (3) The pair should be in the format:
   
   CRM@Gene
   
   For example: (as the input file named input_Test.csv) 
   
   ![](input.jpg)
   
   Note: The input chromosomal regions start from the 5' end.

8. Predict the probability if the given CRM targets the gene.

```
python main.py -i <input_txt_file> -o <output_file_name>
```
>**Required arguments:**
>
>* -i: The input file for CRM-TI.
>
>* -o: The output prediction results.


## Output Results
If we use the following as our inputs with the example command:

![](images/input.png)

```
python main.py -i input_test.txt -o output_test
```

>** output_test:**

![](images/output.png)

Output format explanation:
>* CRM@gene [targeting probability]

