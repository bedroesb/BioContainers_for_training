**STEPS:

Having nextflow in a container:
```
docker pull nextflow/nextflow
```

Running nextflow container and connecting to the outer docker.socket
```    
docker run -v /var/run/docker.sock:/var/run/docker.sock -it nextflow/nextflow 
```

Having all the tools available as containers:
```
docker pull biocontainers/bowtie2:v2.3.1_cv1
docker pull quay.io/biocontainers/cufflinks:2.2.1--py35_2
docker pull quay.io/biocontainers/tophat:2.0.13--py27_2
```
