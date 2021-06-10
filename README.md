# fqcomp
Quality scores compressor using parallel arithmetic code written by Rust.

## Note
Two input Files(input fastq file and parameter json file) are required for program.

The parameter file should contain the following values.
:precision, file_size, thread_num, first_line, last_line

The precision should be set to more than 30 and less than 52.
When compressing, you must enter the value of precision, file_size , and threadnum, and first_line and last_lein can be assigned any value.

For efficient use of threads, it is recommended that the file size be assigned as the number of original quality scores lines divided by greater than 100.

When decompressing, you only need to assign a value to the thread_num , and any value to the other parameters. The name of the input file of decompression exclude the index of the file. For example, if the input file is FCLQC001.enc, only FCLQC is entered

When random access, you only need to assign a value to the thread_num, first_line, last_line , and any value to the other parameters.

Example of parameter file is in the sample_data folder.

## Usage of FCLQC
      cargo.exe [Cargo OPTIONS] [MAIN OPTIONS] [INPUT FILE |OUTPUT NAME| PARAMETER FILE]
      
      MAINT OPTIONS: [-c | -d | -r]  
                    -c : run compressor[default] \n
                    -d : run decompressor\n
                    -r : run random access\n
                    -h : help
### Compress
      cargo.exe -c <INPUT-FILE> <OUTPUT-FILE-NAME> <PARAMETER-FILE> 
      
      Example of runing  compressor in release mode 
      :cargo run --release -- -c input.fastq outputname parameter.json
### Decompress and random acees
      cargo.exe -d(-r) <INPUT-FILE-NAME> <OUTPUT-FILE-NAME> <PARAMETER-FILE>
  
      Example of runing  decompressor in release mode 
      :cargo run --release -- -d inputname outputname parameter.json
           
      Example of runing  randaom access in release mode
      :cargo run --release -- -r inputname outputname parameter.json
                    
                    
                    
