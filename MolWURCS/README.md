# MolWURCS

* Repository: https://gitlab.com/glycoinfo/molwurcs



## Usage

### Options

| option | argument | description |
| ------ | -------- | ----------- |
| -i, --in          | FORMAT=[wurcs\|mdlv2000\|sdf\|mol2\|smi] | Set input format |
| -o, --out         | FORMAT=[wurcs\|mdlv2000\|sdf\|mol2\|smi] | Set output format |
|     --with-aglycone     |             | Set option for outputting WURCS with aglycone |
| -p, --title_property_id | PROPERTY_ID | Use property as title, which key of the value is <PROPERTY_ID> |

### Available Formats
| format | description |
| ------ | ----------- |
| wurcs    | WURCS |
| mdlv2000 | MDLV2000 Format |
| sdf      | SD File |
| mol2     | Mol2 |
| smi      | SMILES |


* Example-1: INPUT: SDF, OUTPUT: WURCS

```
$ java -jar MolWURCS.jar --title_property_id INPUT_WURCS  --in sdf --out wurcs ./test.sdf 
```

* result
```
18:02:31.239 INFO  [main] Converter - Read input as file: ./test.sdf 
18:02:31.288 INFO  [main] MoleculeToWURCSGraph - Start process for molecule: Title 
WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/	WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/ 
```

* input SDF
```
$ cat ./test.sdf  
Title
  CDK     05222118042D

 12 12  0  0  1  0  0  0  0  0999 V2000
   -0.0074   -1.2404    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0
   -1.2978   -0.4954    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0
   -1.2960    1.0277    0.0000 C   0  0  2  0  0  0  0  0  0  0  0  0
    0.0122    1.7736    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0
    1.3026    1.0286    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0
    2.6017    1.7784    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    1.3021   -0.4723    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -0.0023   -2.7404    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -2.5973   -1.2446    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -2.5925    1.7820    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    0.0163    3.2736    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    3.9006    1.0282    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
  1  2  1  0  0  0  0 
  2  3  1  0  0  0  0 
  3  4  1  0  0  0  0 
  4  5  1  0  0  0  0 
  5  6  1  1  0  0  0 
  1  7  1  0  0  0  0 
  1  8  1  1  0  0  0 
  2  9  1  6  0  0  0 
  3 10  1  1  0  0  0 
  4 11  1  6  0  0  0 
  5  7  1  0  0  0  0 
  6 12  1  0  0  0  0 
M  END
> <INPUT_WURCS>
WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/

$$$$
```

* Example-2: INPUT: WURCS, OUTPUT: SDF


```
$ echo "Title    WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/" | java -jar ./MolWURCS.jar -p ID --in wurcs --out sdf 1> test.sdf 
```

* result
```
$ cat ./test.sdf  
Title 
  CDK     05222118042D 

12 12  0  0  1  0  0  0  0  0999 V2000 
   -0.0074   -1.2404    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0 
   -1.2978   -0.4954    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0 
   -1.2960    1.0277    0.0000 C   0  0  2  0  0  0  0  0  0  0  0  0 
    0.0122    1.7736    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0 
    1.3026    1.0286    0.0000 C   0  0  1  0  0  0  0  0  0  0  0  0 
    2.6017    1.7784    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0 
    1.3021   -0.4723    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
   -0.0023   -2.7404    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
   -2.5973   -1.2446    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
   -2.5925    1.7820    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
    0.0163    3.2736    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
    3.9006    1.0282    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0 
  1  2  1  0  0  0  0  
  2  3  1  0  0  0  0  
  3  4  1  0  0  0  0  
  4  5  1  0  0  0  0  
  5  6  1  1  0  0  0  
  1  7  1  0  0  0  0  
  1  8  1  1  0  0  0  
  2  9  1  6  0  0  0  
  3 10  1  1  0  0  0  
  4 11  1  6  0  0  0  
  5  7  1  0  0  0  0  
  6 12  1  0  0  0  0  
M  END 
> <INPUT_WURCS> 
WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/ 

> <ID> 
Title 

$$$$ 
```


* Example-3: INPUT: SDF, OUTPUT: WURCS

```
$ cat ./test.sdf | java -jar ./MolWURCS.jar -p ID --in sdf --out wurcs 
```

* result

```
18:10:15.290 INFO  [main] MoleculeToWURCSGraph - Start process for molecule: Title 
Title	WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/ 
```

* Example-4: INPUT: SDF, OUTPUT: WURCS file

```
$ cat ./test.sdf | java -jar ./MolWURCS.jar -p ID --in sdf --out wurcs 1>wurcs.txt 
```

  * result
```
$ cat wurcs.txt  
Title	WURCS=2.0/1,1,0/[a2122h-1b_1-5]/1/ 
```
