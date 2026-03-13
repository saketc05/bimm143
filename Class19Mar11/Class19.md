# Class 19: Cancer Mutation Analysis
Saket Chodavarapu (PID: A18582086)

``` r
library(bio3d)

seqs <- read.fasta("A18582086_mutant_seq.fa")
head(seqs)
```

    $id
    [1] "wt_healthy"   "mutant_tumor"

    $ali
                 [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12]
    wt_healthy   "M"  "E"  "H"  "Q"  "L"  "L"  "C"  "C"  "E"  "V"   "E"   "T"  
    mutant_tumor "M"  "E"  "H"  "Q"  "L"  "L"  "C"  "C"  "E"  "V"   "E"   "T"  
                 [,13] [,14] [,15] [,16] [,17] [,18] [,19] [,20] [,21] [,22] [,23]
    wt_healthy   "I"   "R"   "R"   "A"   "Y"   "P"   "D"   "A"   "N"   "L"   "L"  
    mutant_tumor "I"   "R"   "R"   "A"   "Y"   "P"   "D"   "A"   "N"   "L"   "L"  
                 [,24] [,25] [,26] [,27] [,28] [,29] [,30] [,31] [,32] [,33] [,34]
    wt_healthy   "N"   "D"   "R"   "V"   "L"   "R"   "A"   "M"   "L"   "K"   "A"  
    mutant_tumor "N"   "D"   "R"   "V"   "L"   "R"   "A"   "M"   "L"   "K"   "A"  
                 [,35] [,36] [,37] [,38] [,39] [,40] [,41] [,42] [,43] [,44] [,45]
    wt_healthy   "E"   "E"   "T"   "C"   "A"   "P"   "S"   "V"   "S"   "Y"   "F"  
    mutant_tumor "E"   "E"   "T"   "C"   "A"   "P"   "S"   "V"   "S"   "Y"   "F"  
                 [,46] [,47] [,48] [,49] [,50] [,51] [,52] [,53] [,54] [,55] [,56]
    wt_healthy   "K"   "C"   "V"   "Q"   "K"   "E"   "V"   "L"   "P"   "S"   "M"  
    mutant_tumor "K"   "C"   "V"   "Q"   "K"   "E"   "V"   "L"   "P"   "S"   "M"  
                 [,57] [,58] [,59] [,60] [,61] [,62] [,63] [,64] [,65] [,66] [,67]
    wt_healthy   "R"   "K"   "I"   "V"   "A"   "T"   "W"   "M"   "L"   "E"   "V"  
    mutant_tumor "R"   "K"   "I"   "V"   "A"   "T"   "W"   "M"   "L"   "E"   "V"  
                 [,68] [,69] [,70] [,71] [,72] [,73] [,74] [,75] [,76] [,77] [,78]
    wt_healthy   "C"   "E"   "E"   "Q"   "K"   "C"   "E"   "E"   "E"   "V"   "F"  
    mutant_tumor "C"   "E"   "E"   "Q"   "K"   "C"   "E"   "E"   "E"   "V"   "F"  
                 [,79] [,80] [,81] [,82] [,83] [,84] [,85] [,86] [,87] [,88] [,89]
    wt_healthy   "P"   "L"   "A"   "M"   "N"   "Y"   "L"   "D"   "R"   "F"   "L"  
    mutant_tumor "P"   "L"   "A"   "M"   "N"   "Y"   "L"   "D"   "R"   "F"   "L"  
                 [,90] [,91] [,92] [,93] [,94] [,95] [,96] [,97] [,98] [,99] [,100]
    wt_healthy   "S"   "L"   "E"   "P"   "V"   "K"   "K"   "S"   "R"   "L"   "Q"   
    mutant_tumor "S"   "L"   "E"   "P"   "V"   "K"   "K"   "S"   "R"   "L"   "Q"   
                 [,101] [,102] [,103] [,104] [,105] [,106] [,107] [,108] [,109]
    wt_healthy   "L"    "L"    "G"    "A"    "T"    "C"    "M"    "F"    "V"   
    mutant_tumor "L"    "L"    "G"    "A"    "T"    "C"    "M"    "F"    "V"   
                 [,110] [,111] [,112] [,113] [,114] [,115] [,116] [,117] [,118]
    wt_healthy   "A"    "S"    "K"    "M"    "K"    "E"    "T"    "I"    "P"   
    mutant_tumor "A"    "S"    "K"    "M"    "K"    "E"    "T"    "I"    "P"   
                 [,119] [,120] [,121] [,122] [,123] [,124] [,125] [,126] [,127]
    wt_healthy   "L"    "T"    "A"    "E"    "K"    "L"    "C"    "I"    "Y"   
    mutant_tumor "L"    "T"    "A"    "E"    "K"    "L"    "C"    "I"    "Y"   
                 [,128] [,129] [,130] [,131] [,132] [,133] [,134] [,135] [,136]
    wt_healthy   "T"    "D"    "N"    "S"    "I"    "R"    "P"    "E"    "E"   
    mutant_tumor "T"    "D"    "N"    "S"    "I"    "R"    "P"    "E"    "E"   
                 [,137] [,138] [,139] [,140] [,141] [,142] [,143] [,144] [,145]
    wt_healthy   "L"    "L"    "Q"    "M"    "E"    "L"    "L"    "L"    "V"   
    mutant_tumor "L"    "L"    "Q"    "M"    "E"    "L"    "L"    "L"    "V"   
                 [,146] [,147] [,148] [,149] [,150] [,151] [,152] [,153] [,154]
    wt_healthy   "N"    "K"    "L"    "K"    "W"    "N"    "L"    "A"    "A"   
    mutant_tumor "N"    "K"    "L"    "K"    "W"    "N"    "L"    "A"    "A"   
                 [,155] [,156] [,157] [,158] [,159] [,160] [,161] [,162] [,163]
    wt_healthy   "M"    "T"    "P"    "H"    "D"    "F"    "I"    "E"    "H"   
    mutant_tumor "M"    "T"    "P"    "H"    "D"    "F"    "I"    "E"    "H"   
                 [,164] [,165] [,166] [,167] [,168] [,169] [,170] [,171] [,172]
    wt_healthy   "F"    "L"    "S"    "K"    "M"    "P"    "E"    "A"    "E"   
    mutant_tumor "F"    "L"    "S"    "K"    "M"    "P"    "E"    "A"    "E"   
                 [,173] [,174] [,175] [,176] [,177] [,178] [,179] [,180] [,181]
    wt_healthy   "E"    "N"    "K"    "Q"    "I"    "I"    "R"    "K"    "H"   
    mutant_tumor "E"    "N"    "K"    "Q"    "I"    "I"    "R"    "K"    "H"   
                 [,182] [,183] [,184] [,185] [,186] [,187] [,188] [,189] [,190]
    wt_healthy   "A"    "Q"    "T"    "F"    "V"    "A"    "L"    "C"    "A"   
    mutant_tumor "A"    "Q"    "T"    "F"    "V"    "A"    "L"    "C"    "A"   
                 [,191] [,192] [,193] [,194] [,195] [,196] [,197] [,198] [,199]
    wt_healthy   "T"    "D"    "V"    "K"    "F"    "I"    "S"    "N"    "P"   
    mutant_tumor "T"    "D"    "V"    "K"    "F"    "I"    "S"    "N"    "P"   
                 [,200] [,201] [,202] [,203] [,204] [,205] [,206] [,207] [,208]
    wt_healthy   "P"    "S"    "M"    "V"    "A"    "A"    "G"    "S"    "V"   
    mutant_tumor "V"    "S"    "M"    "V"    "A"    "A"    "G"    "S"    "V"   
                 [,209] [,210] [,211] [,212] [,213] [,214] [,215] [,216] [,217]
    wt_healthy   "V"    "A"    "A"    "V"    "Q"    "G"    "L"    "N"    "L"   
    mutant_tumor "V"    "A"    "A"    "V"    "Q"    "G"    "E"    "N"    "L"   
                 [,218] [,219] [,220] [,221] [,222] [,223] [,224] [,225] [,226]
    wt_healthy   "R"    "S"    "P"    "N"    "N"    "F"    "L"    "S"    "Y"   
    mutant_tumor "R"    "S"    "P"    "R"    "N"    "F"    "Y"    "S"    "Y"   
                 [,227] [,228] [,229] [,230] [,231] [,232] [,233] [,234] [,235]
    wt_healthy   "Y"    "R"    "L"    "T"    "R"    "F"    "L"    "S"    "R"   
    mutant_tumor "Y"    "R"    "L"    "T"    "R"    "F"    "L"    "S"    "R"   
                 [,236] [,237] [,238] [,239] [,240] [,241] [,242] [,243] [,244]
    wt_healthy   "V"    "I"    "K"    "C"    "D"    "P"    "D"    "C"    "L"   
    mutant_tumor "V"    "I"    "K"    "C"    "D"    "P"    "D"    "C"    "L"   
                 [,245] [,246] [,247] [,248] [,249] [,250] [,251] [,252] [,253]
    wt_healthy   "R"    "A"    "C"    "Q"    "E"    "Q"    "I"    "E"    "A"   
    mutant_tumor "R"    "A"    "C"    "Q"    "E"    "Q"    "I"    "E"    "A"   
                 [,254] [,255] [,256] [,257] [,258] [,259] [,260] [,261] [,262]
    wt_healthy   "L"    "L"    "E"    "S"    "S"    "L"    "R"    "Q"    "A"   
    mutant_tumor "L"    "L"    "E"    "S"    "S"    "L"    "R"    "Q"    "A"   
                 [,263] [,264] [,265] [,266] [,267] [,268] [,269] [,270] [,271]
    wt_healthy   "Q"    "Q"    "N"    "M"    "D"    "P"    "K"    "A"    "A"   
    mutant_tumor "Q"    "Q"    "N"    "M"    "D"    "P"    "K"    "A"    "A"   
                 [,272] [,273] [,274] [,275] [,276] [,277] [,278] [,279] [,280]
    wt_healthy   "E"    "E"    "E"    "E"    "E"    "E"    "E"    "E"    "E"   
    mutant_tumor "E"    "E"    "E"    "E"    "E"    "E"    "E"    "E"    "E"   
                 [,281] [,282] [,283] [,284] [,285] [,286] [,287] [,288] [,289]
    wt_healthy   "V"    "D"    "L"    "A"    "C"    "T"    "P"    "T"    "D"   
    mutant_tumor "V"    "D"    "L"    "A"    "C"    "T"    "P"    "T"    "D"   
                 [,290] [,291] [,292] [,293] [,294] [,295]
    wt_healthy   "V"    "R"    "D"    "V"    "D"    "I"   
    mutant_tumor "V"    "R"    "D"    "V"    "D"    "I"   

    $call
    read.fasta(file = "A18582086_mutant_seq.fa")

``` r
diffs <- seqs$ali[1,] != seqs$ali[2,]

which(diffs)
```

    [1] 200 215 221 224

``` r
seqs$ali[,diffs]
```

                 [,1] [,2] [,3] [,4]
    wt_healthy   "P"  "L"  "N"  "L" 
    mutant_tumor "V"  "E"  "R"  "Y" 

``` r
healthy <- seqs$ali[1,]
mutant <- seqs$ali[2,]
```

``` r
#blast <- blast.pdb(healthy)
```

``` r
#head(blast)
```
