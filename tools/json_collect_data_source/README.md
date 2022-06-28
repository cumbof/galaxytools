This tool exploits the [json_collect_data_source 1.0.0](https://github.com/bioconda/bioconda-recipes/tree/master/recipes/json-collect-data-source) BioConda package to receive multiple datasets (optionally with their metadata) in a single query. As an extension of the [galaxy-json-data-source](https://github.com/mdshw5/galaxy-json-data-source) tool, it allows to handle archives (gz, bz2, tar, and zip) organizing their content in a collection. This feature is optional and can be enabled by setting the ```organize``` parameter to ```true``` in the JSON schema as shown in the example below. If the ```organize``` parameter is setted to ```false```, the archive will be downloaded and added to the history as the other files specified in the JSON schema, but it will not be decompress. This feature works properly if the tool XML schema contains the ```outputs``` block exactly as reported below. The ```collection``` block can be removed but the tool will not be able to organize the content of any archives. Be sure to remove the ```organize``` parameter from any archive entry in the JSON schema or set them to ```false``` if you do not need any collection in output.

#### JSON Schema

```
[ 
  {
     "url":"http://bioinf.iasi.cnr.it/gdcwebapp/example/20170613231507_2217801a-5785-4b43-afe6-398ad061c815/request.xml",
     "name":"GDCWebApp XML Request",
     "extension":"xml"
  },
  {
     "url":"http://bioinf.iasi.cnr.it/gdcwebapp/example/20170613231507_2217801a-5785-4b43-afe6-398ad061c815/request.txt",
     "name":"GDCWebApp Human-Readable Request Summary",
     "extension":"txt"
  },
  {
     "url":"http://bioinf.iasi.cnr.it/gdcwebapp/example/20170613231507_2217801a-5785-4b43-afe6-398ad061c815/dataset-1-gdc.tar.gz",
     "name":"Data Set 1 [GDC]",
     "extension":"gz",
     "metadata":{"db_key":"hg38"},
     "organize":"true"
  },
  {
     "url":"http://bioinf.iasi.cnr.it/gdcwebapp/example/20170613231507_2217801a-5785-4b43-afe6-398ad061c815/dataset-1-bed.tar.gz",
     "name":"Data Set 1 [BED]",
     "extension":"gz",
     "metadata":{"db_key":"hg38"},
     "organize":"true"
  }
]
```
