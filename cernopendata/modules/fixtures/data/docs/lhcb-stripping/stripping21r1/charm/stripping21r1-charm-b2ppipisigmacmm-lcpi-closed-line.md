[[stripping21r1 lines]](./stripping21r1-index)

# StrippingB2ppipiSigmacmm_Lcpi_Closed_Line

## Properties:

|                |                                                 |
|----------------|-------------------------------------------------|
| OutputLocation | Phys/B2ppipiSigmacmm_Lcpi_Closed_Line/Particles |
| Postscale      | 1.0000000                                       |
| HLT            | None                                            |
| Prescale       | 1.0000000                                       |
| L0DU           | None                                            |
| ODIN           | None                                            |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdLooseProtons_Particles

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseProtons](./stripping21r1-commonparticles-stdlooseprotons)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLoosePions_Particles

|      |                                                                                              |
|------|----------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLoosePions](./stripping21r1-commonparticles-stdloosepions)/Particles')\>0 |

DaVinci::N3BodyDecays/threepart_B2ppipiSigmacmm_Lcpi

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLoosePions](./stripping21r1-commonparticles-stdloosepions)' , 'Phys/[StdLooseProtons](./stripping21r1-commonparticles-stdlooseprotons)' ]                                                                                                                                                                                                                                                                                                                                                                                           |
| DaughtersCuts    | { '' : 'ALL' , 'p+' : '(PT\>500.0)&(P\>10000.0) & (TRCHI2DOF\<3.0) & (MIPCHI2DV(PRIMARY)\>8.0) & ((PIDp-PIDpi)\>5.0) & ((PIDp-PIDK)\>-5.0)' , 'pi+' : '(PT\>400.0)&(P\>5000.0) & (TRCHI2DOF\<3.0) & (MIPCHI2DV(PRIMARY)\>8.0) & ((PIDK-PIDpi)\<0.0) & ( TRGHOSTPROB \< 0.3 )' , 'pi-' : '(PT\>400.0)&(P\>5000.0) & (TRCHI2DOF\<3.0) & (MIPCHI2DV(PRIMARY)\>8.0) & ((PIDK-PIDpi)\<0.0) & ( TRGHOSTPROB \< 0.3 )' , 'p~-' : '(PT\>500.0)&(P\>10000.0) & (TRCHI2DOF\<3.0) & (MIPCHI2DV(PRIMARY)\>8.0) & ((PIDp-PIDpi)\>5.0) & ((PIDp-PIDK)\>-5.0)' } |
| CombinationCut   | (AMAXDOCA('')\<0.15) & (APT\>1000.0) & (AM\<2800.0) & (AM\>1500.0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| MotherCut        | (PT\>1000.0) & (VFASPF(VCHI2/VDOF)\<5.0) & (VFASPF(VMINVDCHI2DV(PRIMARY))\>49.0) & (M\<2800.0) & (M\>1500.0) & (MIPCHI2DV(PRIMARY)\>6.0)                                                                                                                                                                                                                                                                                                                                                                                                          |
| DecayDescriptor  | [D+ -\> p+ pi+ pi+]cc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| DecayDescriptors | [ '[D+ -\> p+ pi+ pi+]cc' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Output           | Phys/threepart_B2ppipiSigmacmm_Lcpi/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

LoKi::VoidFilter/SelFilterPhys_StdLooseLambdac2PKPi_Particles

|      |                                                                                                            |
|------|------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseLambdac2PKPi](./stripping21r1-commonparticles-stdlooselambdac2pkpi)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)/Particles')\>0 |

FilterDesktop/pifromSigmamm_B2ppipiSigmacmm_Lcpi

|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
| Code            | (TRCHI2DOF\<3.0) &(PT\>150.0)&(P\>2000.0) &(PT\<1000000.0)&(P\<10000000.0) & (MIPCHI2DV(PRIMARY)\>8.0) |
| Inputs          | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)' ]                    |
| DecayDescriptor | None                                                                                                   |
| Output          | Phys/pifromSigmamm_B2ppipiSigmacmm_Lcpi/Particles                                                      |

CombineParticles/Sigmacmm2LcpiB2ppipiSigmacmm_Lcpi

|                  |                                                                                                                                                                                                                                                   |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdLooseLambdac2PKPi](./stripping21r1-commonparticles-stdlooselambdac2pkpi)' , 'Phys/pifromSigmamm_B2ppipiSigmacmm_Lcpi' ]                                                                                                             |
| DaughtersCuts    | { '' : 'ALL' , 'Lambda_c+' : "(ADMASS('Lambda_c~-')\<100.0) & (VFASPF(VCHI2/VDOF)\<5.0) & (BPVVDCHI2\>36.0) " , 'Lambda_c~-' : "(ADMASS('Lambda_c~-')\<100.0) & (VFASPF(VCHI2/VDOF)\<5.0) & (BPVVDCHI2\>36.0) " , 'pi+' : 'ALL' , 'pi-' : 'ALL' } |
| CombinationCut   | (AMAXDOCA('')\<0.2) & (APT\>0.0)                                                                                                                                                                                                                  |
| MotherCut        | (VFASPF(VCHI2/VDOF)\<10.0) & (BPVVDCHI2\>36.0) & (PT\>0.0) &((M-M1)\>0.0) & ((M-M1)\<1000.0)                                                                                                                                                      |
| DecayDescriptor  | [Sigma_c~-- -\> Lambda_c~- pi-]cc                                                                                                                                                                                                               |
| DecayDescriptors | [ '[Sigma_c~-- -\> Lambda_c~- pi-]cc' ]                                                                                                                                                                                                       |
| Output           | Phys/Sigmacmm2LcpiB2ppipiSigmacmm_Lcpi/Particles                                                                                                                                                                                                  |

CombineParticles/B2ppipiSigmacmm_Lcpi_Closed_Line

|                  |                                                                                           |
|------------------|-------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/Sigmacmm2LcpiB2ppipiSigmacmm_Lcpi' , 'Phys/threepart_B2ppipiSigmacmm_Lcpi' ]    |
| DaughtersCuts    | { '' : 'ALL' , 'D+' : 'ALL' , 'D-' : 'ALL' , 'Sigma_c++' : 'ALL' , 'Sigma_c~--' : 'ALL' } |
| CombinationCut   | (AMAXDOCA('')\<0.2)                                                                       |
| MotherCut        | (ADMASS('B+')\<200.0) & (BPVVDCHI2\>64.0) & (BPVDIRA\>0.998) & (VFASPF(VCHI2/VDOF)\<5.0)  |
| DecayDescriptor  | [B+ -\> Sigma_c~-- D+]cc                                                                |
| DecayDescriptors | [ '[B+ -\> Sigma_c~-- D+]cc' ]                                                        |
| Output           | Phys/B2ppipiSigmacmm_Lcpi_Closed_Line/Particles                                           |
