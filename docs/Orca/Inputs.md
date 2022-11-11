# Standard Inputs
## Routine Screening
!!! note
    Optimize with *Gaussian style*-B3LYP and 6-31G* and do TDDFT (PBE0 def2-SVP, 30 roots) afterwards
```
! B3LYP/G DEF2/J RIJCOSX 6-31g* OPT FREQ PAL6
%maxcore 2000
%output
Print[p_mos] true
Print[p_basis] 3
End
* xyzfile 0 1 <Add xyz file here>

$new_job

! PBE0 def2-svp DEF2/J RIJCOSX
%tddft
nroots 30
end 
```