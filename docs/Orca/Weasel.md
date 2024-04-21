# Weasel Keywords
## Options

| Keyword |  Description |
|---|---|
|  `-h, --help`   |   show this help message and exit   |  
|  `-v, -version, --version`   |   <br> show program's version number and exit   |  
|  `-settingsfile F`   |   Use project settings. Give filename with absolute path.   |  
|  `-postprocess`   |   Do only post-processing, i.e. do not run the actual jobs. Output files should be present.   |  
|  `-restart RESTART`   |   Restart a previously partially finished job. The entire job folder should still be available. Job is restarted where incomplete output files are present.   |  
|  `-overwrite`   |   Overwrite existing files and folders with the same basename.   |  
|  `-no-overwrite`   |   Do not overwrite any files and folders with the same basename. If a mainjob folder with the same basename exists and new one with an additional index number will be created (e.g. '<basename>_1').   |  

## Structures

Primary chemical structure(s) used for calculations. filename Structure file with a single or multiple structures: Allowed formats : xyz, mol2, pdb, sdf, mae, smi and inchi

| Keyword |  Description |
|---|---|
|  `-smiles SMILES [SMILES ...]`   |   <br> Provide input structure(s) as list of SMILES strings. Multiple SMILES strings should be separated by spaces.   |  
|  `-inchi INCHI [INCHI ...]`   |   <br> Provide input structure(s) as list of InChI strings. Multiple InChIs strings should be separated by spaces.   |  
|  `-atom ATOM [ATOM ...]`   |   <br> Pass a single atom as input. Multiple atoms can be separated by spaces. The charge and multiplicity can be set via '-c' and '-m', respectively. All atoms will receive the same charge and multiplicity!   |  

## Workflows

Standard workflows. (Custom workflow directory can be set via environment variable WEASEL_WORKFLOW_DIR)

| Keyword |  Description |
|---|---|
|  `-workflow W, -W W`   |   Available workflows are: AIQU-ConfSearch, AIQU- ConfSearch-Extended, AIQU-ConfSearch-Extended-v2, AIQU-ConfSearch-v2, AIQU-NMS, AIQU-NMS-Extended, AIQU- SP-ExcitedState, AIQU-SP-Solvent, CCS, CCS-Deprot- Ensemble, CCS-Prot-Ensemble, ChemSearch-Deprot, ChemSearch-HAT, ChemSearch-IonBinding, ChemSearch- Prot, ChemSearch-Prot-Docker, ChemSearch-Tautomer, ConfSearch, ConfSearch-ActiveSite, ConfSearch-TS, Docking-Water, ExcitedState-Analysis, ExcitedState- Opt, HostGuestLED, InteractionEnergy, NormalModeSampling, OptimalBinding, React, React_water, Reactivity, Reactivity-Explore, Spectrum- IR, Spectrum-IR-Ensemble, Spectrum-NMR, Spectrum-NMR- Ensemble, Spectrum-Raman, Spectrum-Raman-Ensemble, Spectrum-UVVisCD, Spectrum-UVVisCD-Ensemble   |  
|  `-workflow-file WORKFLOW_FILE`   |   <br> path to custom workflow file.   |  

## System Settings

| Keyword |  Description |
|---|---|
|  `-keeptopo`   |   Keep the topology (i.e. atom connectivity and bond orders) of the input structure(s) if available.   |  
|  `-no-keeptopo`   |   Discard any topology info (i.e. atom connectivity and bond orders) given in the input structures.   |  
|  `-mirror`   |   Mirror all conformer structures that do not have a chiral center.   |  
|  `-no-mirror`   |   Don't mirror all conformer structures that do not have a chiral center.   |  
|  `-c C, -charge C`   |   System charge C   |  
|  `-enforcefilecharge`   |   Total charged defined in structure file, SMILES or InChI is used, instead of the one defined via '-c/-charge' or in the settings/workflow file.   |  
|  `-no-enforcefilecharge`   |   <br> Ignore Total charged defined in structure file, SMILES or InChI is used. (This switch is only relevant if enforcing of file charges is turned on by default in the settings/workflow file!   |  
|  `-m M, -mult M`   |   System multiplicity M   |  
|  `-temp T`   |   Temperature T in Kelvin   |  
|  `-pressure P`   |   Pressure P in atm   |  

## Basic Workflow Options

| Keyword |  Description |
|---|---|
|  `-opt-sp`   |   Optimization and SP energy calculation   |  
|  `-sponly`   |   Only do SP calculation, no optimization   |  
|  `-optts-activeatoms A [A ...]`   |   <br> Active atoms of transition state, i.e. atoms that are involved in reaction.   |  
|  `-optts-activeatoms-template A [A ...]`   |   <br> Active atoms of transition state of template Hessian (specified via -optts-inputhessian), i.e. atoms that are involved in reaction.   |  
|  `-preopt`   |   Switch on preoptimization   |  
|  `-no-preopt`   |   Switch off preoptimization   |  
|  `-opt`   |   Switch on optimization   |  
|  `-no-opt`   |   Switch off optimization and preoptimization   |  
|  `-correctimagmodes`   |   Rerun optimization in case (unwanted) imaginary modes are found with the frequency analysis.   |  
|  `-no-correctimagmodes`   |   Do not rerun optimization in case (unwanted) imaginary modes are found with the frequency analysis.   |  
|  `-opt-convergence {Sloppy,Loose,Normal,Tight,VeryTight}`   |   <br> Convergence level used for optimization. Allowed options are: Sloppy, Loose, Normal, Tight, VeryTight   |  
|  `-opt-calcinitialhess`   |   Calculate an initial exact Hessian before optimizations   |  
|  `-opt-retry`   |   Try to convergence a non-converged optimization by running a few extra cycles.   |  
|  `-opt-no-retry`   |   Do not try to convergence a non-converged optimization by any means.   |  
|  `-spdft`   |   Do a final DFT single point calculation   |  
|  `-no-spdft`   |   Switch off DFT single point calculation   |  
|  `-spdft-grad`   |   Compute gradient in DFT single point calculation   |  
|  `-no-spdft-grad`   |   Switch off gradient calculation in DFT single point calculation   |  
|  `-optts`   |   do TS optimization   |  
|  `-optts-inputhessian INPUTHESSIAN`   |   <br> Input hessian of (previously optimized) TS structure. Needs to be an ORCA Hessian file.   |  
|  `-spwf`   |   Switch on Post-HF single point calculation   |  
|  `-no-spwf`   |   Switch off Post-HF single point calculation   |  
|  `-scants`   |   Do relaxed surface scan and subsequent TS optimization   |  
|  `-freq`   |   Compute vibrational frequencies at the end of a (TS) optimization   |  
|  `-no-freq`   |   Do not compute vibrational frequencies, e.g. at the end of a (TS) optimization   |  
|  `-irc`   |   Compute intrinsic reaction coordinate   |  
|  `-no-irc`   |   Do not compute intrinsic reaction coordinate, e.g. at the end of a TS optimization   |  
|  `-sn SN`   |   Rotational symmetry number. Overwriting the automatically detected rotational symmetry number.   |  
|  `-reactivity-en`   |   Compute electro- and nucleophilicity   |  
|  `-uhf`   |   Force unrestricted calculation   |  
|  `-no-d3`   |   Switch off D3   |  
|  `-fukui`   |   Compute Fukui function on DFT SP level.   |  

## Methods

| Keyword |  Description |
|---|---|
|  `-preopt-method M`   |   Method used for preoptimization. Allowed options M are: XTB, XTB1, XTB-FF, HF-3c, PBEh-3c, B97-3c, r2SCAN-3c, AM1, PM3, MNDO   |  
|  `-preopt-keeptopology`   |   The connectivity of the input structure cannot change during preoptimization.   |  
|  `-no-preopt-keeptopology`   |   <br> The connectivity of the input structure can change during preoptimization.   |  
|  `-opt-method M`   |   Method used for optimization. Allowed options M are: BP86, TPSS, PBE, B97M-D3BJ, B3LYP, B3LYP/G, BHANDHLYP, PW6B95, PBE0, wB97X, wB97X-V, wB97M-V, CAM-B3LYP, B2PLYP, DLPNO-B2PLYP, B2GP-PLYP, DLPNO-B2GP-PLYP, DSD- PBEP86, DLPNO-DSD-PBEP86, DSD-PBEP86/2013, DLPNO-DSD- PBEP86/2013, R2SCAN, M062X, MP2, DLPNO-MP2, SCS-MP2, RIJDX-MP2, RIJDX-DLPNO-MP2, RIJDX-SCS-MP2, RIJK-MP2, RIJK-DLPNO-MP2, RIJK-SCS-MP2, XTB, XTB1, XTB-FF, HF-3c, PBEh-3c, B97-3c, r2SCAN-3c, AM1, PM3, MNDO   |  
|  `-spdft-method M`   |   Method used for DFT single point calculation. Allowed options M are: BP86, TPSS, PBE, B97M-D3BJ, B3LYP, B3LYP/G, BHANDHLYP, PW6B95, PBE0, wB97X, wB97X-V, wB97M-V, CAM-B3LYP, B2PLYP, DLPNO-B2PLYP, B2GP-PLYP, DLPNO-B2GP-PLYP, DSD-PBEP86, DLPNO-DSD-PBEP86, DSD- PBEP86/2013, DLPNO-DSD-PBEP86/2013, R2SCAN, M062X, HF-3c, PBEh-3c, B97-3c, r2SCAN-3c, AM1, PM3, MNDO   |  
|  `-spwf-method M`   |   Method used for Post-HF single point calculation. Allowed options M are: HF, MP2, SCS-MP2, CCSD, CCSD(T), DLPNO-MP2, DLPNO-CCSD, BP-DLPNO-CCSD, DLPNO- CCSD(T), BP-DLPNO-CCSD(T), RIJDX-HF, RIJDX-MP2, RIJDX- SCS-MP2, RIJDX-DLPNO-MP2, RIJDX-DLPNO-CCSD(T), RIJK- HF, RIJK-MP2, RIJK-SCS-MP2, RIJK-DLPNO-MP2, RIJK- DLPNO-CCSD(T), CCSD_T, DLPNO-CCSD_T, BP-DLPNO-CCSD_T, RIJDX-DLPNO-CCSD_T, RIJK-DLPNO-CCSD_T   |  
|  `-spwf-pno P PNO`   |   Settings for Post-HF single point calculation. Allowed options P are: Loose, Normal, Tight, Normal_TightPairs, LooseIntra_NormalTightPairsForInteraction, LooseIntra_TightForInteraction, NormalIntra_NormalTightPairsForInteraction, NormalIntra_TightForInteraction   |  
|  `-spdft-pno P PNO`   |   Settings for DLPNO-DHDFT single point calculation. Allowed options P are: Loose, Normal, Tight   |  
|  `-opt-pno P PNO`   |   Settings for DLPNO-DHDFT optimizations. Allowed options P are: Loose, Normal, Tight   |  
|  `-no-cosx`   |   Do not use COSX approximation   |  
|  `-rijk`   |   Use RIJK approximation   |  
|  `-conf-no-keeptstopo`   |   The connectivity of the TS active atoms can change during optimization.   |  
|  `-conf-preopt-method M`   |   <br> Method used for preoptimization in conformational search. Allowed options see: see: -preopt-method   |  
|  `-conf-looseopt-method M`   |   <br> Method used for loose optimization in conformational search. Allowed options see: -opt-method   |  
|  `-conf-opt-method M`   |   Method used for optimization in conformational search. Allowed options see: -opt-method   |  
|  `-conf-spdft-method M`   |   Method used for DFT single point calculation in conformational search. Allowed options see: -spdft- method   |  
|  `-conf-spwf-method M`   |   Method used for Post-HF single point calculation in conformational search. Allowed options see: -spwf- method   |  
|  `-nmr-coupling-method M`   |   <br> Method used for NMR J-coupling calculation. Allowed options see: -spdft-method   |  

## Basis Sets

| Keyword |  Description |
|---|---|
|  `-opt-basis BAS`   |   Basis used for optimization. Allowed options BAS are: *MiniX, SV, SV(P), SVP, TZVP, TZVPP, old-SV, old-SV(P), old-SVP, old-TZVP, old-TZVPP, def2-SV(P), def2-SVP, def2-TZVP, def2-TZVP(-F), def2-TZVPP, def2-QZVP, def2-QZVPP, ma-def2-SV(P), ma-def2-SVP, ma-def2-TZVP, ma-def2-TZVP(-F), ma-def2-TZVPP, ma-def2-QZVP, ma- def2-QZVPP, def2-SVPD, def2-TZVPD, def2-TZVPPD, def2-QZVPD, def2-QZVPPD, ZORA-SV(P), ZORA-SVP, ZORA- TZV(P), ZORA-TZVP, ZORA-TZVPP, ZORA-def2-SV(P), ZORA- def2-SVP, ZORA-def2-TZVP, ZORA-def2-TZVP(-F), ZORA- def2-TZVPP, ZORA-def2-QZVPP, old-ZORA-SV(P), old-ZORA- SVP, old-ZORA-TZV(P), old-ZORA-TZVP, old-ZORA-TZVPP, ZORA-ma-def2-SV(P), ZORA-ma-def2-SVP, ZORA-ma- def2-TZVP, ZORA-ma-def2-TZVP(-F), ZORA-ma-def2-TZVPP, ZORA-ma-def2-QZVPP, DKH-SV(P), DKH-SVP, DKH-TZV(P), DKH-TZVP, DKH-TZVPP, DKH-def2-SV(P), DKH-def2-SVP, DKH-def2-TZVP, DKH-def2-TZVP(-F), DKH-def2-TZVPP, DKH- def2-QZVPP, old-DKH-SV(P), old-DKH-SVP, old-DKH- TZV(P), old-DKH-TZVP, old-DKH-TZVPP, DKH-ma- def2-SV(P), DKH-ma-def2-SVP, DKH-ma-def2-TZVP, DKH-ma- def2-TZVP(-F), DKH-ma-def2-TZVPP, DKH-ma-def2-QZVPP, SARC-DKH-TZVP, SARC-DKH-TZVPP, SARC-ZORA-TZVP, SARC- ZORA-TZVPP, cc-pVDZ, cc-pVTZ, cc-pVQZ, cc-pV5Z, cc- pV6Z, aug-cc-pVDZ, aug-cc-pVTZ, aug-cc-pVQZ, aug-cc- pV5Z, aug-cc-pV6Z, pcSseg-0, pcSseg-1, pcSseg-2, pcSseg-3, pcSseg-4, pcJ-0, pcJ-1, pcJ-2, pcJ-3, pcJ-4, 6-31+G\*, 6-31+G\*\*, 6-31G\*, 6-31G\*\*, 6-311+G\*\**   |  
|  `-spdft-basis BAS`   |   Basis used for DFT single point calculation. Allowed options see: -opt-basis   |  
|  `-spwf-basis BAS`   |   Basis used for Post-HF single point calculation. Allowed options see: -opt-basis   |  
|  `-opt-basis2 BAS`   |   Extra basis used for optimization. Allowed options see: -opt-basis   |  
|  `-spdft-basis2 BAS`   |   Extra basis used for DFT single point calculation. Allowed options see: -opt-basis   |  
|  `-spwf-basis2 BAS`   |   Extra basis used for Post-HF single point calculation. Allowed options see: -opt-basis   |  
|  `-basis2-atoms A [A ...]`   |   <br> Atoms that are described by the extra basis. Atom index ranges can be defined via A-B or A- (up to end of system).   |  
|  `-conf-looseopt-basis BAS`   |   <br> Basis used for loose optimization in conformational search. Allowed options see: -opt-basis   |  
|  `-conf-opt-basis BAS`   |   Basis used for optimization in conformational search. Allowed options see: -opt-basis   |  
|  `-conf-spdft-basis BAS`   |   <br> Basis used for DFT single point calculation in conformational search. Allowed options see: -opt-basis   |  
|  `-conf-spwf-basis BAS`   |   Basis used for Post-HF single point calculation in conformational search. Allowed options see: -opt-basis   |  
|  `-nmr-coupling-basis BAS`   |   <br> Basis used for NMR J-coupling calculation. Allowed options see: -spdft-basis   |  

## Implicit Solvation

| Keyword |  Description |
|---|---|
|  `-solvent SOL`   |   Define solvent to be used with implicit solvation model. If explicit solvation is turned on, it will use the same solvent as defined through the explict solvation, as long as no custom explicit solvent is specified. Allowed options SOL are: *Acetone, Acetonitrile, Ammonia, Benzene, CCl4, CH2Cl2, CHCl3, Chloroform, Cyclohexane, DMF, DMSO, Ethanol, H2O, Hexane, Infinity, Methanol, NH3, Octanol, Protein, Pyridine, THF, Tetrahydrofuran, Toluene, Water*   |  
|  `-solvent-spwf-method TYPE`   |   <br> define method to be used with implicit solvation model + coupled cluster. Allowed options are: None, PTE, PTE(S), PTES   |  
|  `-gas`   |   Switch off solvent   |  
|  `-smd`   |   Use implicit solvent SMD   |  
|  `-cpcm`   |   Use implicit solvent CPCM (using COSMO epsilon function).   |  

## Explicit Solvation

| Keyword |  Description |
|---|---|
|  `-solvent-expl [XYZFILE]`   |   <br> Perform explicit solvation. The default solvent is the same one used for implicit solvation. If implicit solvation is turned off, water will be used as solvent.Optionally a different explicit solvent can be read from XYZFILE.   |  
|  `-solvent-no-explicit`   |   Turn off explicit solvation.   |  
|  `-solvent-expl-only [XYZFILE]`   |   <br> Only perform explicit solvation of solute and exit. The default solvent is the same one used for implicit solvation. If implicit solvation is turned off, water will be used as solvent. Optionally a different explicit solvent can be read from XYZFILE.   |  
|  `-solvent-expl-method {docking,stochastic}`   |   <br> Method used for explicit solvation.   |  
|  `-solvent-expl-nsolv N`   |   <br> Number of solvent molecules to be added.   |  
|  `-solvent-expl-fixsolute`   |   <br> Keep the geometry of the solute fixed during explicit solvation.   |  
|  `-solvent-expl-no-fixsolute`   |   <br> Do not keep the geometry of the solute fixed during explicit solvation.   |  
|  `-solvent-expl-charge N`   |   <br> Total charge of solvent molecule.   |  
|  `-solvent-expl-mult N`   |   Multiplicity of solvent molecule.   |  
|  `-solvent-expl-maxrad N`   |   <br> Fixed maximum radius for the explicit solvent [Ang].   |  
|  `-solvent-expl-droplet`   |   <br> Enforce a spherical arrangement of solvent molecules around the solute.   |  
|  `-solvent-expl-no-droplet`   |   <br> Do not enforce a spherical arrangement of solvent molecules around the solute.   |  
|  `-solvent-expl-auto-sp-method M`   |   <br> Method M used for DFT single point calculations used to evaluate which solvent molecules are strongly bound. Allowed options see: -spdft-method   |  
|  `-solvent-expl-auto-sp-basis BAS`   |   <br> Basis set BAS used for DFT single point calculations used to evaluate which solvent molecules are strongly bound. Allowed options see: -opt-basis   |  
|  `--solvent-expl-auto-sp-final-method M`   |   <br> Method M used for DFT single point calculations used to evaluate the final binding energy solute and solvents. Allowed options see: -spdft-method   |  
|  `-solvent-expl-auto-sp-final-basis BAS`   |   <br> Basis set BAS used for DFT single point calculations used to evaluate the final binding energy solute and solvents. Allowed options see: -opt-basis   |  
|  `-solvent-expl-auto-maxmol N`   |   <br> Maximum number of explicit solvent molecules to be added. By default 150% of the number of atoms in the solute molecule is the upper limit. But at least 10 molecules.   |  
|  `-solvent-expl-auto-batchsize N`   |   <br> Number of explicit solvent molecules added per solvation cycle after the first cycle.   |  
|  `-solvent-expl-auto-inibatch N`   |   <br> Number of explicit solvent molecules added in the first solvation cycle. By default this value is set to the square root of the number of atoms in the solute molecule is used. But a minimum of 5 solvent molecule will be added in the first cycle.   |  
|  `-solvent-expl-auto-thresh N`   |   <br> Energy threshold (in kcal/mol) below which solvent molecules are considered strongly bound.   |  

## Hardware

| Keyword |  Description |
|---|---|
|  `-cores N`   |   Number of cores N for parallel run   |  
|  `-hostfile HOSTFILE`   |   hostfile containing hostnames of reserved nodes (only for calculations on computer cluster).   |  
|  `-mem`   |   N[unit] Available memory per core. Allowed SI unit suffixes: B, K, M, G, T [default: M]. Units are interpreted as powers of 1000 (SI format).   |  
|  `-mem-total`   |   N[unit] Available memory for all cores. Allowed SI unit suffixes: B, K, M, G, T [default: M]. Units are interpreted as powers of 1000 (SI format).   |  

## Output Options

| Keyword |  Description |
|---|---|
|  `-no-write-xyz`   |   write a summary xyz file to the main job dir and for a confsearch workflow intermediate ensembles to the ConfSearch folder.   |  
|  `-write-mae, -write-maestro`   |   <br> write a summary maestro file to the main job dir and for a confsearch workflow intermediate ensembles to the ConfSearch folder.   |  
|  `-write-sdf`   |   write a summary sdf file to the main job dir and for a confsearch workflow intermediate ensembles to the ConfSearch folder.   |  
|  `-verbosesummary`   |   write a verbose version of the summary file.   |  
|  `-label L`   |   Directory label for where calculation output is stored. Label is added to basename.   |  
|  `-outputmolversion {V2000,V3000}`   |   <br> Define mol version used for output of sdf files. [Default: if the structure file is a sdf file, then the same version like in the file is used, otherwise V3000.]   |  
|  `-reportdir REPORT_DIR`   |   <br> Write a copy of the report files to REPORT_DIR. Can also be set via $WEASEL_REPORT_DIR.   |  
|  `-basename BASENAME`   |   Set a basename for the current job. Normally Weasel determines the basename automatically from the input parameters.   |  
|  `-energyunit`   |   eU Unit for energy in reporting. Allowed options eU are: Eh, J, J/mol, au, cal, cal/mol, eV, kJ, kJ/mol, kcal, kcal/mol, keV   |  
|  `-chargetype cT [cT ...]`   |   <br> Population scheme that is used for charge printing in mol2 file. Not used for SP_WF calculations. Allowed options cT are: CHELPG, Hirshfeld, Loewdin, Mulliken, all   |  
|  `-storecharges`   |   Store charges specified via -chargetype in charges.txt file.   |  
|  `-storewfx`   |   Store wfx and wfx file for SPDFT calculations.   |  
|  `-compress {files,folders}`   |   <br> Choose a compression mode. Modes: 'files'=Only compress large files; 'folders'=Tar and compress all calculation dirs.   |  
|  `-no-compress`   |   Disable compression.   |  

## Relaxed Surface Scan Options

| Keyword |  Description |
|---|---|
|  `-scan-bond A A`   |   Bond definition for relaxed surface scan. A1 A2.   |  
|  `-scan-angle A A A`   |   Angle definition for relaxed surface scan. A1 A2 A3.   |  
|  `-scan-dihedral A A A A`   |   <br> Dihedral definition for relaxed surface scan. A1 A2 A3 A4.   |  
|  `-scan-start V`   |   Start value V for scan   |  
|  `-scan-stop V`   |   End value V for scan   |  
|  `-scan-nsteps N`   |   Number of steps N for scan   |  

## Constraints Options

| Keyword |  Description |
|---|---|
|  `-constrain-cartesians A [A ...]`   |   <br> Constrain the current Cartesian coordinates of selected atoms. Atoms can either specified by their atom type (element), by their atom id or by a ranges of atom ids: "-constrain-cartesians C H 1 2 5-8" would constrain all carbon and hydrogen atoms, as well as the atoms 1, 2, 5, 6, 7 and 8. Counting of atoms usually starts from 1.   |  
|  `-constrain-bonds A1[:A2[:Value]] [A1[:A2[:Value]] ...]`   |   <br> Constrain selected bonds. If only the first atom A1 is specified all bonds to that atom are constrained. The single atom can either by specified by its id (counting usually starts from 1) or by its atom type (element). If the latter syntax is used all atoms of that type are considered. If A1 and A2 are specified the bond between these two atoms is constrained to the current value. Alternatively the bond length in Angstrom can be given as third argument Value. Multiple constraints can be specified as list: e.g. "-constraint-bond C 1:2 3:4:2.0" would constraint all bonds to atoms of type C, the bond between atom 1 and 2 and constrain the bond between atom 3 and 4 to 3.0 Angstrom. If multiple constraints are defined that overlap, then only the last one is considered!   |  
|  `-constrain-angles A1:[Value]|A1:A2:A3:[Value] [A1:[Value]|A1:A2:A3:[Value] ...]`   |   <br> Constrain selected angles. If only a single atom A1 is specified all angles where A1 is the central atoms are constrained. Alternatively a specific angle can be specified by providing all three atoms A1, A2 and A3. Atoms are specified by their atomic id. Counting usually starts from 1. Angles are expected to be given in degrees. The items within a single constraint statement have to be separated by ":". The Value is optional. If Value is not specified the current value(s) of the angle(s) are used. Multiple constraint can be specified at once, by separating the statements by spaces: E.g. "-constrain-angles 1:2:3 5:6:7:120 8 9:50 " would constrain the angle between atoms 1, 2 and 3 to its current value, the angle formed by 5, 6 and 7 to 120°, all angles that have atom 8 as central atom to their current value and all angles that have atom 5 as central atom to 50°. If multiple constraints are defined that overlap, then only the last one is considered!   |  
|  `-constrain-dihedrals A1:A2:[Value]|A1:A2:A3:A4:[Value] [A1:A2:[Value]|A1:A2:A3:A4:[Value] ...]`   |   <br> Constrain selected dihedrals. If only two atoms A1 and A2 are specified all dihedrals where A1-A2 is the central bond are constrained. Alternatively a specific dihedral can be specified by providing all four atoms A1, A2, A3 and A4. Atoms are specified by their atomic id. Counting usually starts from 1. Dihedrals are expected to be given in degrees. The items within a single constraint statement have to be separated by ":". The Value is optional. If it is not specified the current value(s) of the dihedrals(s) are used. Multiple constraints can be specified at once, by separating the statements by spaces: E.g. "-constrain- dihedrals 1:2:3:4 5:6:7:8:109.4 9:10 11:12:123" would constrain the dihedral formed by atoms 1, 2, 3 and 4 to its current value, the dihedral formed by 5, 6, 7 and 8 to 109.4°, all dihedrals that have the atoms 9 and 10 as central atoms to their current values and all dihedrals that have the atoms 11 and 12 as central atoms to 123.0°. If multiple constraints are defined that overlap, then only the last one is considered!   |  
|  `-opth`   |   optimize hydrogen positions only.   |  
|  `-constrain-xtbonly`   |   Apply constraints only when using XTB level optimization. Can be useful when XTB is too inaccurate for specific bonds   |  

## Plot Options

| Keyword |  Description |
|---|---|
|  `-plot-mo N [N ...]`   |   Plot Molecular Orbital Number N1 N2 for DFT SP calculation.   |  
|  `-plot-ed`   |   Plot Electron Density for DFT SP calculation.   |  
|  `-plot-sd`   |   Plot Spin Density for DFT SP calculation.   |  
|  `-plot-lumo`   |   Plot LUMO for DFT SP calculation.   |  
|  `-plot-homo`   |   Plot HOMO for DFT SP calculation.   |  
|  `-plot-somo, -plot-somos`   |   <br> Plot SOMOs for DFT SP calculation.   |  
|  `-plot-fmos`   |   Plot HOMO and LUMO for DFT SP calculation.   |  
|  `-plot-fmos-upto PLOTFMOSUPTO`   |   <br> Plot frontier orbitals for DFT SP calculation. Number defines the HOMOs and LUMOs in both directions.   |  
|  `-grid-res N`   |   Grid resolution, i.e. number of grid points per Angstrom (x, y and z direction) for plots (MOs, ED, SD).   |  
|  `-grid-x N`   |   Number of grid points in x direction for plots (MO, ED, SD).   |  
|  `-grid-y N`   |   Number of grid points in y direction for plots (MO, ED, SD).   |  
|  `-grid-z N`   |   Number of grid points in z direction for plots (MO, ED, SD).   |  
|  `-grid-xmin N`   |   Minimum dimension on the x axis in Angstrom.   |  
|  `-grid-ymin N`   |   Minimum dimension on the y axis in Angstrom.   |  
|  `-grid-zmin N`   |   Minimum dimension on the z axis in Angstrom.   |  
|  `-grid-xmax N`   |   Maximum dimension on the x axis in Angstrom.   |  
|  `-grid-ymax N`   |   Maximum dimension on the y axis in Angstrom.   |  
|  `-grid-zmax N`   |   Maximum dimension on the z axis in Angstrom.   |  
|  `-grid-xyzmin N`   |   Minimum dimension on x, y and z axis in Angstrom.   |  
|  `-grid-xyzmax N`   |   Maximum dimension on x, y and z axis in Angstrom.   |  
|  `-plot-format P`   |   Output format for plots (MO, ED, SD). Allowed options P are: cube, vis   |  
|  `-spectrum-npoints N`   |   Number of data points for generating spectrum plots.   |  
|  `-spectrum-lineshape {GAUSSIAN,LORENTZIAN}`   |   <br> Lineshape function for spectrum peak broadening.   |  
|  `-spectrum-linewidth L`   |   <br> Linewidth for spectrum plots (in eV for UV/Vis/CD, 1/cm for IR/Raman, Hz for NMR).   |  

## BSSE Options

| Keyword |  Description |
|---|---|
|  `-bsse`   |   Do BSSE calculation.   |  
|  `-bsse-gcp`   |   Do a BSSE calculation using the DFT-D3-gCP scheme.   |  
|  `-bsse-bb`   |   Do a BSSE calculation using the Boys-Bernardi scheme.   |  
|  `-no-bsse`   |   Do not do a BSSE calculation (even if defined in settings).   |  
|  `-bsse-c C1 C2 C1 C2`   |   Only applicable if the docker is NOT used: Charges C1 and C2 for the two molecules of BSSE calculation. C1 is for the larger molecule (1), C2 for the smaller molecule (2). If both molecules consist of the same number of atoms, the molecule the first atom of the system belongs to is molecule 1. Default is system charge / 2.   |  
|  `-bsse-m M1 M2 M1 M2`   |   Only applicable if the docker is NOT used: Multiplicities M1 and M2 for the two molecules of BSSE calculation. For ordering see bsseC. Default: Unpaired electrons of system are divided equally onto both molecules.   |  
|  `-bsse-dimercalcsonly`   |   Do only the calculations for the dimer part, i.e. no monomer calculations.   |  
|  `-bsse-freezemonomers BSSE`   |   calculation: Do not separately optimize the monomers, but instead use their geometries in the complex.   |  
|  `-bsse-optimizemonomers`   |   <br> BSSE calculation: Do separately optimize the monomers.   |  

## Host-GuestAtom LED Options

| Keyword |  Description |
|---|---|
|  `-hg-led`   |   Do host-guest LED calculation.   |  
|  `-no-hg-led`   |   Do not do a host-guest LED calculation (even if defined in settings).   |  
|  `-hg-led-dimercalcsonly`   |   <br> Do only the calculations for the dimer part, i.e. no monomer calculations.   |  
|  `-hg-led-freezemonomers`   |   <br> Host-guest LED calculation: Do not separately optimize the monomers, but instead use their geometries in the complex.   |  
|  `-hg-led-optimizemonomers`   |   <br> Host-guest LED calculation: Do separately optimize the monomers.   |  
|  `-hg-led-addguest AddGuest [AddGuest ...]`   |   <br> Add guest molecule to host: Need structure file. Optional: 1) Charge of the guest: -C <charge> (default 0). 2) Multiplicity of the guest: -M <multiplicity> (default 1).   |  

## Converger Options

| Keyword |  Description |
|---|---|
|  `-prescf`   |   Converge the SCF with an approximate SCF before the actual SP energy calculation   |  
|  `-no-prescf`   |   Do not converge the SCF with an approximate SCF before the actual SP energy calculation   |  
|  `-scf-retry`   |   Try to recover non-convergence SCF calculation by rerunning the SCF calculation with different SCF acceleration strategies (see the '-badconvX' options for more details).   |  
|  `-scf-no-retry`   |   Do not try to recover a non-converged SCF calculation.   |  
|  `-no-badconv`   |   Turn off any convergence accelerator ('-badconvX' switches) and use ORCA's internal defaults.   |  
|  `-badconv1`   |   Convergence accelerator when SCF convergence is very slow with default settings. Invokes a smaller level shift.   |  
|  `-badconv2`   |   Convergence accelerator when SCF is fluctuating with default settings. Increases damping, recomputes Fock matrix after each iteration to reduce numerical noise.   |  
|  `-badconv3`   |   Convergence accelerator when the SCF is unstable and oscillating with default settings. Invokes a large level shift.   |  
|  `-badconv4`   |   Convergence accelerator for very tricky open-shell systems. Performs first a small basis followed by the final basis calculation.   |  
|  `-scf-trah-autotrah`   |   Enable ORCA's AutoTRAH feature. AutoTRAH triggers TRAH if a SCF is not converged after N cycles. N can be set with '--scf-trah-autoiter'.   |  
|  `-scf-trah-no-autotrah`   |   <br> Disables ORCA's AutoTRAH.   |  

## Relativistics

| Keyword |  Description |
|---|---|
|  `-zora`   |   Use ZORA for treatment of relativistic effects.   |  
|  `-dkh`   |   Use DKH for treatment of relativistic effects.   |  
|  `-ecp`   |   Use ECPs for treatment of relativistic effects.   |  
|  `-no-rel`   |   Do not use scalar relativistics / ECPs.   |  

## Reactivity

| Keyword |  Description |
|---|---|
|  `-reactivity-nebts`   |   Find TS with NEB-TS Feature   |  
|  `-product PRODUCT`   |   File with product structure for finding TS.   |  
|  `-tsguess TSGUESS`   |   File with TS guess structure for finding TS (optional).   |  
|  `-neb-usemepguess`   |   Use guess for minimum energy path in NEB calculation. Guess provided in ORCA's allxyz file format as input structure file.   |  
|  `-neb-fixends`   |   Reactant and product structure should be kept as they are.   |  
|  `-neb-sp-onlyts`   |   If requested, compute SP and frequency only for TS structure. (Not yet functional.)   |  
|  `-neb-sp-fullreaction`   |   If requested, compute SP and frequency for reactant, TS, and product.)   |  
|  `-neb-boost`   |   Use Fast-NEB-TS to boost the convergence. Comes with slightly lower robustness.   |  
|  `-neb-nimages NEB_NIMAGES`   |   <br> Use this number of images for the NEB calculation.   |  
|  `-irc-nsteps IRC_NSTEPS`   |   <br> Use this maximum number of steps for each direction of the IRC calculation.   |  
|  `-irc-inputhessian IRC_INPUTHESSIAN`   |   <br> Input hessian of (previously optimized) TS structure for IRC calculation. Needs to be an ORCA Hessian file.   |  

## Normal Mode Sampling

| Keyword |  Description |
|---|---|
|  `-nms`   |   Do a Normal Mode Sampling (NMS)   |  
|  `-no-nms`   |   Switch off Normal Mode Sampling (NMS)   |  
|  `-nms-nstruc NMSNSTRUC`   |   <br> Number of structures to generate with NMS   |  
|  `-nms-nmodes NMSNMODES`   |   <br> Number of normal modes to use for the displacement   |  
|  `-nms-temp NMSTEMP`   |   Temperature used in normal mode sampling   |  
|  `-nms-unit {regular,unitless}`   |   <br> Units of the normal modes used   |  
|  `-nms-usegaussianw`   |   Use Gaussian weights on top of the regular Ri   |  
|  `-nms-sigma NMSSIGMA`   |   Sigma value for the Gaussian weight (in cm-1)   |  
|  `-nms-minfreq NMSMINFREQ`   |   <br> Minimum frequency of mode to include (in cm-1)   |  

## UV/Vis and CD calculation

| Keyword |  Description |
|---|---|
|  `-uvvis`   |   Start TDDFT calculation for UV/Vis spectrum prediction.   |  
|  `-es-states TDDFT_NROOTS`   |   <br> Number of excited states considered for UV/Vis / CD spectrum prediction.   |  
|  `-es-soc`   |   Compute Spin-Orbit-Coupling between the states.   |  
|  `-es-analyzestates TDDFT_ANALYZE_ROOTS [TDDFT_ANALYZE_ROOTS ...]`   |   <br> Which excited states should be analyzed? Options: All, or provide a list of integers.   |  
|  `-es-densityanalysis {None,Unrelaxed,Relaxed,Both}`   |   <br> Which density should be used for excited state population analysis (atomic charges, bond orders)? Options:None, Unrelaxed, Relaxed, Both   |  
|  `-es-opt`   |   Optimize to excited state.   |  
|  `-es-opt-state TDDFT_OPT_STATE`   |   <br> Optimize to excited state.   |  
|  `-es-opt-triplet`   |   Optimize to triplet state in excited state optimization (for singlet ground states).   |  
|  `-tddft-tda`   |   Use TDA approximation for TDDFT.   |  
|  `-tddft-no-tda`   |   Do not use TDA approximation for TDDFT.   |  

## IR calculation

| Keyword |  Description |
|---|---|
|  `-ir`   |   Compute IR spectrum   |  
|  `-raman`   |   Compute Raman spectrum (also implies IR)   |  
|  `-ir-scalefreq F`   |   Scale the harmonic frequencies by F before generating IR/Raman spectra   |  

## NMR Properties

| Keyword |  Description |
|---|---|
|  `-nmr [{element,all} ...]`   |   <br> Compute NMR chemical shifts for a list of elements or "all". If no element is defined, default is H and C.   |  
|  `-nmr-ref-h NMR_REF_H NMR`   |   reference for H: value in ppm or structure file.   |  
|  `-nmr-ref-c NMR_REF_C NMR`   |   reference for C: value in ppm or structure file.   |  
|  `-nmr-ref-n NMR_REF_N NMR`   |   reference for N: value in ppm or structure file.   |  
|  `-nmr-ref-si NMR_REF_SI`   |   <br> NMR reference for Si: value in ppm or structure file.   |  
|  `-nmr-ref-p NMR_REF_P NMR`   |   reference for P: value in ppm or structure file.   |  
|  `-nmr-ref-{x} NMR_REF_X`   |   <br> NMR reference (value in ppm or structure file) for another element. Replace {x} with an element symbol in lowercase.   |  
|  `-nmr-coupling [{element,all} ...]`   |   <br> Compute NMR indirect spin-spin couplings for a list of elements or "all". If no element is defined, default is H.   |  

## Collision Cross Section

| Keyword |  Description |
|---|---|
|  `-ccs`   |   Do a Collision Cross Section Calculation (CCS).   |  
|  `-no-ccs`   |   Switch off Collision Cross Section Calculation (CCS)   |  
|  `-ccs-cluster`   |   Do a geometrical clustering before CCS calculations   |  
|  `-ccs-no-cluster`   |   Switch off geometrical clustering before CCS calculations   |  
|  `-ccs-maxcycles CCSMAXCYCLES`   |   <br> Maximum number of cycles to run with CCS   |  
|  `-ccs-mincycles CCSMINCYCLES`   |   <br> Minimum number of cycles to run with CCS   |  
|  `-ccs-velocity CCSVELOCITY`   |   <br> Number of velocities to run with CCS   |  
|  `-ccs-impact CCSIMPACT`   |   <br> Number of impact integration points to run with CCS   |  
|  `-ccs-gas {He,N2}`   |   Type of collision gas to run with CCS. Allowed options are: He, N2   |  
|  `-ccs-sem CCSSEM`   |   Relative deviation of the standard error of the mean.   |  
|  `-ccs-slope CCS_SLOPE`   |   Slope value for linear calibration of CCS values.   |  
|  `-ccs-offset CCS_OFFSET`   |   <br> Offset value for calibration of CCS values.   |  

## Conformational Search

| Keyword |  Description |
|---|---|
|  `-confsearch`   |   Run conformational search analysis.   |  
|  `-no-confsearch`   |   Switch off conformational search analysis.   |  
|  `-confsearchts`   |   Run conformational search analysis on transition state.   |  
|  `-no-confsearchts`   |   Switch off conformational search analysis on transition state.   |  
|  `-conf-finaltsfreq`   |   Compute frequencies on lowest-energy TS conformer.   |  
|  `-conf-keeptstopo`   |   The connectivity of the TS active atoms should not change drastically during optimization.   |  
|  `-conf-gen-method {crest,crest-rdkit,crestff,crestff-gfn2,crestff-gfn2-rdkit,crestff-rdkit,goat,goatff,rdkit,read,rdkit}`   |   <br> Method for conformer generation in conformer search. Allowed options are: CREST, CREST-RDKIT, CRESTFF, CRESTFF-GFN2, CRESTFF-GFN2-RDKIT, CRESTFF-RDKIT, GOAT, GOATFF, RDKIT, READ, RDKIT   |  
|  `-conf-quick`   |   Switch on the quick conformational search.   |  
|  `-conf-gen-screenintermolbinding`   |   <br> Generate conformers for noncovalently bound complexes. Currently only works together with CREST.   |  
|  `-conf-gen-nruns CONF_GEN_NRUNS`   |   <br> Number of conformer generation runs that are carried out for creating the initial conformer ensemble.   |  
|  `-conf-gen-preseed`   |   Generate a diverse set of initial structures as input for the different ConfGen-Runs using RDKit.   |  
|  `-conf-gen-no-preseed`   |   Do not generate a diverse set of initial structures as input for the different ConfGen-Runs using RDKit.   |  
|  `-conf-gen-maxnconf CONF_GEN_MAXNCONF`   |   <br> Maximum number of conformers generated before starting filtering steps.   |  
|  `-conf-gen-enrange CONF_GEN_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers kept in conformer generation.   |  
|  `-conf-preopt`   |   Use preoptimization step for conformational search.   |  
|  `-conf-no-preopt`   |   Switch off preoptimization step for conformational search.   |  
|  `-conf-preopt-enrange CONF_PREOPT_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after preoptimization step.   |  
|  `-conf-opt`   |   Use optimization step for conformational search.   |  
|  `-conf-no-opt`   |   Switch off optimization step for conformational search.   |  
|  `-conf-opt-enrange CONF_OPT_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after optimization step.   |  
|  `-conf-opt-store-trj CONF_OPT_STORETRJ [CONF_OPT_STORETRJ ...]`   |   <br> Store geometries and gradients of optimization trajectory steps A1 A2 ...   |  
|  `-conf-looseopt`   |   Carry out an additional preoptimization using approximate Opt level settings.   |  
|  `-conf-no-looseopt`   |   Switch off additional preoptimization using approximate Opt level settings   |  
|  `-conf-looseopt-enrange CONF_LOOSEOPT_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after loose optimization step.   |  
|  `-conf-correctimagmodes`   |   <br> Rerun optimization conformational search in case (unwanted) imaginary modes are found with the frequency analysis.   |  
|  `-conf-no-correctimagmodes`   |   <br> Do not rerun optimization conformational search in case (unwanted) imaginary modes are found with the frequency analysis.   |  
|  `-conf-spdft`   |   Use DFT single point calculation step for conformational search.   |  
|  `-conf-no-spdft`   |   Switch off DFT single point calculation step for conformational search.   |  
|  `-conf-spdft-enrange CONF_DFT_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after DFT calculation step.   |  
|  `-conf-spwf`   |   Use Post-HF single point calculation step for conformational search.   |  
|  `-conf-no-spwf`   |   Switch off Post-HF single point calculation step for conformational search.   |  
|  `-conf-spwf-enrange CONF_WF_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after Post-HF calculation step.   |  
|  `-conf-gibbscorrection`   |   <br> Use enthalpic and entropic correction for optimization, SP_DFT and SP_WF steps.   |  
|  `-conf-no-gibbscorrection`   |   <br> Do not use enthalpic and entropic correction for optimization, SP_DFT and SP_WF steps.   |  
|  `-conf-maxnconf CONF_MAXNCONF`   |   <br> Maximum number of conformers that are kept at the end of the conformer search.   |  
|  `-conf-keep {lowest,all}`   |   <br> Which conformer(s) to keep for subsequent steps after the conformer search.   |  
|  `-conf-initialfiltering`   |   <br> Use initial filtering step for rotamers or identical conformers for conformational search.   |  
|  `-conf-no-initialfiltering`   |   <br> Switch off initial filtering step for rotamers or identical conformers for conformational search.   |  
|  `-conf-initialfiltering-enrange CONF_INITFILTER_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of conformers after initial filtering step.   |  
|  `-conf-torsionfilter A A A A`   |   <br> Use initial torsion angle filtering step for conformational search. Torsion angle definition for filtering initial conformer ensemble. A1 A2 A3 A4.   |  
|  `-conf-torsionfilter-range V V`   |   <br> Torsion angle range (in degrees) which should be considered for conformational search. Filter checks for V1 <= dihedral <= V2, with dihedral defined between -180 and 180 degrees   |  
|  `-conf-rmsd-print`   |   print files with RMSD of conformers after preoptimization and optimization step in conformational search.   |  
|  `-conf-enantiomer`   |   The conformation search will be done using the mirror image of the input molecule.   |  
|  `-conf-filterchiral`   |   The filtering step will make sure that the stereochemistry of the input is kept.   |  
|  `-conf-rmsd-method {graph,RDKit,basic}`   |   <br> What method level should be used to compute the RMSD during screening?   |  
|  `-conf-rmsd-thresh CONF_SCREENINGRMSD_THRESH`   |   <br> RMSD for identical structures in screening.   |  
|  `-conf-rmsd-tscorethresh CONF_SCREENINGRMSD_TSCORETHRESH`   |   <br> RMSD for identical TS core structures in screening.   |  
|  `-conf-strictconvergence`   |   <br> Enforce strict convergence during optimizations.   |  
|  `-conf-keeprotamers`   |   Keep all rotamers coming found by CREST in the ensemble?   |  
|  `-conf-only-spdft`   |   Only compute DFT single point energies on provided conformer ensemble, nothing else. These energies are then used for Boltzmann weighting in the following property calculation. Has to be combined with -conf- gen-method READ.   |  
|  `-conf-only-spwf`   |   Only compute Post-HF single point energies on provided conformer ensemble, nothing else. These energies are then used for Boltzmann weighting in the following property calculation. Has to be combined with -conf- gen-method READ.   |  
|  `-conf-scf-retry`   |   Turn on the automatic SCF-recovery in the conformer search procedure if a SCF calculation fails. This keyword overrides the global '-scf[-no]-retry' keywords within the conformer search procedure.   |  
|  `-conf-scf-no-retry`   |   Turn off the automatic SCF-recovery in the conformer search procedure if a SCF calculation fails. This keyword overrides the global '-scf[-no]-retry' keywords within the conformer search procedure.   |  
|  `-conf-opt-retry`   |   Try to convergence a non-converged optimization of a conformer in the conformer search procedure by running a few extra cycles. This keyword overrides the global '-opt[-no]-retry' keywords within the conformer search procedure.   |  
|  `-conf-opt-no-retry`   |   Do not try to convergence a non-converged optimization of a conformer in the conformer search procedure by any means. This keyword overrides the global '-opt[-no]-retry' keywords within the conformer search procedure.   |  
|  `-conf-cluster`   |   [{fine,coarse,coarse1,coarse2,coarse3,coarse4}] Do a clustering step after screening. As optional argument the clustering mode can be provided [default: fine]   |  
|  `-conf-no-cluster`   |   Do a clustering step after screening.   |  
|  `-conf-cluster-nmax CONF_CLUSTER_NMAX`   |   <br> Define a maximum number of final clusters. Default is inf.   |  
|  `-conf-cluster-elevel {PreOpt,Opt}`   |   <br> What method level should be used for the clusering approach?   |  
|  `-conf-ignorehs`   |   Ignore H-atoms for conformer screening.   |  
|  `-conf-no-ignorehs`   |   Include H-atoms for conformer screening.   |  

## GOAT - used in ConfSearch only

| Keyword |  Description |
|---|---|
|  `-goat-explore`   |   Set GOAT-EXPLORE option for a complete search with free topology.   |  
|  `-goat-entropy`   |   Set GOAT-ENTROPY option to enforce convergence of conformational entropy.   |  
|  `-goat-diversity`   |   Set GOAT-DIVERSITY option to focus on geometrical diversity.   |  
|  `-goat-react`   |   Set GOAT-REACT option to allow for full PES search (still experimental!).   |  
|  `-goat-react-maxtopodiff CONF_GOAT_MAXTOPODIFF`   |   <br> Define the maximum topological difference for a GOAT- REACT run (default 8 - still experimental!).   |  
|  `-goat-nworkers CONF_GOAT_NWORKERS`   |   <br> Define the number of workers used in the GOAT. Default is AUTO.   |  
|  `-goat-freefragments`   |   Free topology between different fragments   |  
|  `-goat-freezeamides`   |   Freeze cis/trans amide chirality change when using GOAT.   |  
|  `-goat-freezecistrans`   |   Freeze cis/trans double bond chirality change when using GOAT.   |  
|  `-goat-maxcn ID/ELEMENT:CN [ID/ELEMENT:CN ...]`   |   <br> For conformer searcher with GOAT, constrain maximum coordination number (CN) for individual atoms. Two syntaxes are allowed to specify the max CN: 1) ID:CN, e.g. 3:4, where ID is the position of the atom in the input file (counting starts from 1) and CN is the coordination number; 2) ELEMENT:CN, e.g. Mn:5, where all atoms of type ELEMENT will have a maximum CN of 5. To specify multiple entries, separate them by spaces: e.g. 5:3 C:4 ...   |  
|  `-goat-scaleiter GOAT_SCALEITER`   |   <br> Define the scaling factor for the number of GOAT optimizations.   |  

## Chemical Space Search

| Keyword |  Description |
|---|---|
|  `-anionsearch`   |   Run an anion search analysis (anion = conjugated base).   |  
|  `-no-anionserach`   |   Switch off anion search analysis.   |  
|  `-tautomersearch`   |   Run a tautomer search analysis.   |  
|  `-no-tautomersearch`   |   Switch off tautomer search analysis.   |  
|  `-ibsearch`   |   Run an ion binding site search analysis. Needs to accompanied by the ion that is added, e.g. Ni2+.   |  
|  `-no-ibsearch`   |   Switch off ion binding site search analysis.   |  
|  `-ion ION`   |   Ion used in ion binding site search (IBSearch) analysis, e.g. Ni2+.   |  
|  `-hatsearch`   |   Run a structure search analysis for H-atom abstraction sites.   |  
|  `-no-hatsearch`   |   Switch off structure search analysis for H-atom abstraction sites.   |  
|  `-chemspace-gen-enrange CHEMSPACE_GEN_ENRANGE`   |   <br> Maximum energy range (kcal/mol) of chemical compounds kept in chemical space generation.   |  
|  `-chemspace-smilesfilter`   |   <br> Turn on filtering of topologically equivalent structures based on their canonical SMILES.   |  
|  `-chemspace-no-smilesfilter`   |   <br> Turn off filtering of topologically equivalent structures based on their canonical SMILES.   |  
|  `-protsearch`   |   Run a protomer search analysis.   |  
|  `-no-protsearch`   |   Switch off protomer search analysis.   |  

## Ensemble Workflow

| Keyword |  Description |
|---|---|
|  `-boltzmannaverage`   |   Calculate Boltzmann-weighted average properties or spectra using multiple structures from input or conformer search (with CONF_NFinal > 1).   |  

## Software Settings

| Keyword |  Description |
|---|---|
|  `-scratchdir DIR`   |   set a scratch directory for your WEASEL job.   |  

## Multiscale Simulations

| Keyword |  Description |
|---|---|
|  `-ms-setup`   |   Set up multiscale system, without running actual calculations.   |  
|  `-ms-qmmm`   |   Run QMMM calculation, including on-the-fly setup.   |  
|  `-ms-setup-interactive`   |   <br> Set up multiscale system interactively.   |  
|  `-ms-enforce-input-charge`   |   <br> After multiscale setup do not update QM region charge, but use user input charge   |  
|  `-ms-orcafffile ORCAFF`   |   <br> ORCA forcefield file, accompanying structure file.   |  
|  `-ms-qc-add-res R [R ...]`   |   <br> Residues defining core region of QM region. Can be residue name or residue ID. If the residue name occurs more than once in the pdb file, only the residue ID is accepted - but this can be given for multiple residues. If the residue ID occurs more than once, the corresponding segment (SEG) needs to be defined as well via SEG-ID.   |  
|  `-ms-qc-add-atom A [A ...]`   |   <br> Atoms defining core region of QM region. Can be atom name or atom ID. If the atom name occurs more than once in the pdb file, only the atom ID is accepted - but this can be given for multiple atoms.   |  
|  `-ms-qc-ext-by X`   |   QM region is constructed by extending QM core region by X Angstrom.   |  
|  `-ms-qc-ext-by-full-res`   |   <br> Extend QM core region by full residues.   |  
|  `-ms-qc-ext-by-sc`   |   Extend QM core region by side chains only.   |  
|  `-ms-qc-ext-by-polar-groups`   |   <br> Extend QM core region by polar groups only, ignoring nonpolar side chains.   |  
|  `-ms-qc-ext-by-polar-interactions`   |   <br> Extend QM core region by polar interactions only, e.g. hydrogen bonds and salt bridges.   |  
|  `-ms-qc-ext-no-autocorrect`   |   <br> Switch off automatic check for MM backbone gaps between neighboring QM sidechains or QM backbones. Checks whether less than three bonds separate two QM/MM boundaries.   |  
|  `-ms-qr-add-atom A [A ...]`   |   <br> Add atom to automatically generated QM region. Can be atom name or atom ID.   |  
|  `-ms-qr-add-res R [R ...]`   |   <br> Add residues to automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-add-sc R [R ...]`   |   <br> Add side chains to automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-add-bb R [R ...]`   |   <br> Add backbone to automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-rm-atom A [A ...]`   |   <br> Add atom to automatically generated QM region. Can be atom name or atom ID.   |  
|  `-ms-qr-rm-res R [R ...]`   |   <br> Remove residues from automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-rm-sc R [R ...]`   |   <br> Remove side chains from automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-rm-bb R [R ...]`   |   <br> Remove backbone from automatically generated QM region. Can be residue name or residue ID.   |  
|  `-ms-qr-file F`   |   Atoms for QM region are provided via a file.   |  
|  `-ms-ac-add-res R [R ...]`   |   <br> Residues defining core region of active region. Can be residue name or residue ID. If the residue name occurs more than once in the pdb file, only the residue ID is accepted - but this can be given for multiple residues. If the residue ID occurs more than once, the corresponding segment (SEG) needs to be defined as well via SEG-ID.   |  
|  `-ms-ac-add-atom A [A ...]`   |   <br> Atoms defining core region of active region. Can be atom name or atom ID. If the atom name occurs more than once in the pdb file, only the atom ID is accepted - but this can be given for multiple atoms.   |  
|  `-ms-ac-ext-by X`   |   Active region is constructed by extending active core region by X Angstrom.   |  
|  `-ms-ac-ext-by-wat-and-h`   |   <br> Extend active core region by water residues and hydrogens only.   |  
|  `-ms-ac-ext-by-h`   |   Extend active core region by hydrogens only.   |  
|  `-ms-ac-ext-by-sc-and-bb-sep`   |   <br> Extend active core region by side chain and backbone groups separately.   |  
|  `-ms-ac-ext-by-full-res`   |   <br> Extend active core region by full residues.   |  
|  `-ms-ar-fixbb`   |   Extend active core region by side chains only.   |  
|  `-ms-ar-add-atom A [A ...]`   |   <br> Add atom to automatically generated active region. Can be atom name or atom ID.   |  
|  `-ms-ar-add-res R [R ...]`   |   <br> Add residues to automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-add-sc R [R ...]`   |   <br> Add side chains to automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-add-bb R [R ...]`   |   <br> Add backbone to automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-rm-atom A [A ...]`   |   <br> Remove atom from automatically generated active region. Can be atom name or atom ID.   |  
|  `-ms-ar-rm-res R [R ...]`   |   <br> Remove residues from automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-rm-sc R [R ...]`   |   <br> Remove side chains from automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-rm-bb R [R ...]`   |   <br> Remove backbone from automatically generated active region. Can be residue name or residue ID.   |  
|  `-ms-ar-cut-bb-option T`   |   <br> Scheme for cutting backbone in active core and region. Allowed options are: chemical, residueDefinition   |  
|  `-ms-ac-eq-to-qc`   |   For active core region use the same atoms/residues as for the QM core region.   |  
|  `-ms-ar-eq-to-qr`   |   For active region use the same atoms/residues as for the QM region.   |  
|  `-ms-ar-file F`   |   Atoms for active region are provided via a file.   |  

## Host-Guest Docking

| Keyword |  Description |
|---|---|
|  `-dock GUEST [GUEST ...]`   |   <br> Determine best binding position of a single or multiple guests to a host system. GUEST is xyzfile with one or more guests. Multiple xyzfile can be specified, by separating them with spaces. The charge and multiplicity are of each invidual guest is read from the comment line of the entry in the xyzfile(s). Therefore, the comment line must contain exactly two integers, where the first is the charge and second one the multiplicity.   |  
|  `-no-dock`   |   Disable docking procedure.   |  
|  `-dock-only GUEST [GUEST ...]`   |   <br> This keyword has the same function as '-dock', but it also turns off any other workflow.   |  
|  `-dock-nrepeat N`   |   Add guest(s) N times in docking process. Guests are read repeated in the order the order they were read.   |  
|  `-dock-guest-charge DOCK_GUEST_CHARGE`   |   <br> Set the total charge for every guest structure. By default the charge is read from the first column of the XYZ comment line (if present).   |  
|  `-dock-guest-mult DOCK_GUEST_MULT`   |   <br> Set multiplicity for every guest structure. By default the multiplicity is read from the second column of the XYZ comment line (if present).   |  
|  `-dock-level {normal,quick,screening,complete}`   |   <br> Level of sophistication used for docking.   |  
|  `-dock-bondfactor N`   |   Bonding factor N (e.g 1.5), by which the sum of the radii of host and guest is scaled. If the intermolecular distance is below this value, host and guest are considered to be bound.   |  
|  `-dock-fixhost`   |   Keep the geometry of the host fixed during docking.   |  
|  `-dock-no-fixhost`   |   Do not keep the geometry of the host fixed during docking.   |  

## Bee

| Keyword |  Description |
|---|---|
|  `-bee-workflow ID`   |   Load workflow from Bee in order to update.   |  
|  `-bee-conf ID [ID ...]`   |   <br> Load list of conformers from Bee.   |  

## Conformational Entropy

| Keyword |  Description |
|---|---|
|  `-ensemblethermo`   |   Compute the conformational entropy of the energetically lowest conformer.   |  
|  `-no-ensemblethermo`   |   Do not compute the conformational entropy of the energetically lowest conformer.   |  

## Remove Duplicates

| Keyword |  Description |
|---|---|
|  `-rmduplicates`   |   Remove duplicate structures. Checks are done after reading the input structure, the pre-optimization, and the optimization.   |  

---

© Copyright 2023, FAccTs.

[www.orcasoftware.de](https://www.orcasoftware.de/tutorials_weasel/first_steps/help.html#structures-keywords)