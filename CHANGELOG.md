# **Changelog**

All changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

# beta  versions

## 0.2.3 - 2021-06-17

### Added

- Define new contact for Patella (Knees)
- New positioned model: 50F_Pedestrian_TB024
- Added shoes for 50F

### Changed

- Updated documentation
- Fixed *DATABASE_HISTORY_NODE_LOCAL_ID definitions in *reference_points.k 

## 0.2.2 - 2021-04-13

### Added

- Added the seated male 50M
- Added sex parameter
- Added density, ligament, muscle length and head mass parameters dependent on sex parameter
- Added material angles for skin PIDs 103002, 203002, 305111, 305121, 305131, 305141, 305161, ...
- ... 355111, 355121, 355131, 355141, 355161, 406001, 456001, 506001, 556001, 606001, 656001, ...
- ... 705111, 705121, 705131, 705141, 755111, 755121, 755131, 755141 to remove LS-DYNA warning
- Added cortical bone for the patella PID 751301
- Added constrained rigid bodies between patella shells (7x1301) and solids (7x1302)
- Added surface to surface contact 300001 (UX_Elbox_Surface_to_surface_temp_contact)
- Added set_part 316013 for new contact 300001 (UX_Elbox_Surface_to_surface_temp_contact)
- Added new include (vivaplus-elements.k) and moved all elements to it

### Changed

- Updated node file and main file for 50F standing to version 0.2.2
- Removed PRCA on mat fabric (was giving warning in LS-DYNA)
- Changed density and YM of mat null MID 305104 and 404001 (only density), 454001 (only density)
- Changed density of MID 305122 (Upper extremity tissue) to 1.0e-6
- Changed MID 405100 (thorax soft tissue) ; added density parameter (sex based), and updated viscous parameters to OSCCAR report
- Changed MID 405101 (lung) to lung material definitions and material model according to RATER (2013)
- Changed MID 505001 (abdomen) to Naseri avg response from OSCCAR report
- Added L0 parameter on MID 702411
- Changed MID 705001 (lower extremity soft tissue) to Naseri avg response from OSCCAR project
- Changed MID 710401 (patella cortical) to rigid
- Trimmed curve definition 305101 (skin properties) to get rid of LS-DYNA warnings about curve discretisation error
- Morphed geometry around C7-T1 facet joints to make it more similar to the other CV facet joints.
- Changed thickness of PID 201174 (C7 null shells) to 0.6mm (same as other CV null shells)
- Changed thickness of PID 401212 (TX-Vertebra-Articular-Process-T1-Superior-Null-L) to 0.25mm (same as other CV null shells)
- Changed contact thickness OPTT to 0.5mm for PID 201573 NE-ligaments-C7-T1-CL-M
- Changed MID for PID 305142 and 355142 (Lower arm tissue) to 405100 (Thorax soft tissue)
- Changed element formulation, NIP and SHRF for PID 403601 and 453601 (TX-Ribcage-Cartilage-Exterior) to 2 to improve stability
- Changed MID for PID 405001 and 455001 (Thorax cavity) to 405101 (RATER lung material)
- Chnaged PID 603110 and 653110 (PE-Hip-Ligament-Shell) element form to 9 and NIP to 1 to conform to MAT_FABRIC
- Changed MID for PID 705112 and 755112 (LX-Soft-Thigh-Pelvis-connect-Tissue) to 705001 (Hosein material)
- Changed tied contact 403505 to _OFFSET
- Changed parts in contact 400001 (TX_C_Thorax_pelvis_interior_main) by adding 404400 and 454400 (TX-Intercostal-muscle-Intermost)
- Changed content of Set 716002 to include newly created patella shells. Set used by contact 903001 (Whole body contact)
- Changed DEFINE_CURVE_FUNCTION definitions for knee ligaments to include ssex based scaling
- Changed LS-DYNA format for solid elements to 960 format
- Changed format for load curves on second row of *ELEMENT_DISCRETE_LCO to I8I8
- Changed contact 600001 to _OFFSET

### Removed

- Control cards removed from model (added to separate control file)

## 0.2.1 - 2020-12-23

### Added

- Added prestretch in knee ligaments
- Added tiebreak sliding contact between thorax soft tissue and rib cage
- Control cards in `vivaplus-controls.k`
- Added `PART_CONTACT` for ligaments in the neck (fixes SMP issues)
- Dynasaur metadata for postprocessing (model/postprocess)
- PIPER metadata for positioning (model/preprocess)

### Changed

- Tied lower part of abdominal soft tissue to pelvis
- Adjusted hourglass settings to reduce hourglass energies
- Changed material parameters for thorax soft tissue to the fat tissue model from Naseri's thesis
- Material properties of femur bone
- Internal Contacts
- Material properties of Knee Ligaments
- Corrected CSYS for sternoclavicular joint
- Thoracic and Lumbar intervertebral Discrete beam joint MIDs and curves renumbered

### Removed

- Validation setups removed from model directory (will be moved to Validation Catalogue)
- Eyelid from global contact (causing instabilty)

## 0.2.0 - 2020-09-10

## Added

- Reference landmark nodes for Dynasaur postprocessing

## Changed

- Refactor Include file structure
  - sub-include extension changed from `.key` to `.k`
  - PIDs transferred to body region include files
  - MID names updated with references
  - ID renumbered

# alpha (unreleased) versions

## 0.1.6 - 2020-08-21

### Added

- Added constrain_rigid_bodies between 751703-751701, 754113-754111, 704113-704111, 701703-701701, 351201-351202, 301201-301202
  301101-301102, 351101-351102
- Created extra node sets constraining the patella, scapula, clavicula, talus and Calcaneus to the soft tissue
- Re-pasted Quadriceps to femur (L+R)
- Added null shells covering the external Intercostal muscles (PID 404001 and 454001)
- Added PART_CONTACT OPTT=1mm to PIDs 301201, 351201, 301101, 351101
- Added contact between scapula+Clavicula and ribcage+skin (depenetrated to 1mm)
- Added CONSTRAINED_INTERPOLATION to Quadriceps insertion of femur head to distribute force
- Added a new PID (103005) for the eyelids (ELFORM=16, MAT Elastic E=0.002GPa)


### Changed

- Rotated head seatbelt accelerometer to lay in frankfurt plane
- Changed MID 701701, 9000030, 610411, 610412, 351201, 301201 351201, 301102, 301101, 710402 to MAT_RIGID
- Changed Humerus, Femur, Tibia, Fibula cortical soli elements to ELFORM=2 (and removed HG definition)
- Modified humerus cortical thickness by offseting the nodes, now 3-4mm at shaft
- Changed Pubic Symphysis solid elements to ELFORM=2 (and corrected spelling error in PID name)

### Removed

- Removed all constrained_lagrange_in_solid definitions
- Removed muscle activation for LX-Knee-Muscle-Quadriceps-Femoris-L and LX-Knee-Muscle-Quadriceps-Femoris-R

## 0.1.5 - 2020-07-01

### Added
- Cortical solid layer in the femur head, neck, trochanter

### Changed
- Change to ISO Coordinate system (Rotated model about z-axis by 180 degrees)

## 0.1.4 - 2020-07-01

### Changed
- Updated PIDs 
  - Cervical, Thoracic, Lumbar spine
- New includes for Head and Neck

## 0.1.3 - 2020-06-22

### Added
- Added defualt HG (type 2) to solid parts with ELFORM=1 and previously without HG control

### Changed
- Changed PID 603110 and 653110 (Hip-Ligament-Shell) NIP to 2
- Changed solid rib previously modelled with ELFORM=-1 to ELFORM=1 and added default HG type 2
- Updated PiD information to be more consistent; Rigid and Null shell parts -> ELFORM=2, NIP=2
- contn. SKIN -> ELFORM=9, NIP=1, Cortical bone -> ELFORM=16, NIP=5, HGTYPE=8

### Removed
- Removed unused PID and MID cards
- Removed unused DEFINE_COORDINATE_SYSTEMS
- Removed unused DEFINE_CURVES
- Removed unused nodes
- Removed unused sets

## 0.1.2 - 2020-06-10

### Added

- Added curve 601001 for compressive bahaviour for material 601001 (PE-Cortical_bone_Kemper_2008), and removed PT=0.6 defintion
- Created beam set 2000013 including all neck nuscles for output into ELOUT
- Cross sectional area of NE_L_Stylohyoid_Ligament was missing. Temporary set it to 4mm2 (based on volume and length)
- added PIDs 705114, 755114, 603110 and 653110 to SET 3000001 (contact 400001 - TX_C_Thorax_pelvis_interior_main)

### Changed
- changed ELFORM to 1 for PID 203001 (NE_C_Neck_Soft_Tissues), and updated PR to 0.4999983 on material card
- Change following `*DEFINE_TABLE` definitions by removing copied curves (first and last) 2004072, 2004073, 2004074, 2004075, 2004076, 2004077, 2004082, 2004083, 2004084, 2004085, 2004086, 2004087, 2004092, 2004093, 2004094, 2004095, 2004096, 2004097, 2004112, 2004113, 2004114, 2004115, 2004116, 2004117
- Updated spine tied contact interfaces once more - some loose null mat elements and nodes shared between master and slave was still remaning
- Updated PID 351421 (UX-Bone-Ulna-shaft-Cortical-L) to have PART_CONTACT definition t=1mm (was missing)
- Changed abiscissa values for curve 601001 to be one order of magnitude lower
- Changed material for PID 103002 (HE_C_Head-Skin) to MID 916001 (Skin_Flynn_et_al_2015)
- Change element formulation to 1 for PID 103001 (HE_C_Face_and_Scalp), and added HG control 2000000

### Removed
- Deleted unused coordinate systems 600000-600005
- removed `*CONSTRAINED_INTERPOLATION` definitions related to neck muscles as they didn't work as intended
- Removed `*CONSTRAINED_INTERPOLATION` definition 9000000 and updated first node in `*DEFINE_COORDINATE_NODES_DIR_Z` 701460 - Tibialfibula
- Removed `*CONSTRAINED_INTERPOLATION` definition 9000070 and updated first node in `*DEFINE_COORDINATE_NODES_DIR_Z` 9500018 - Tibialfibula

## 0.1.1 - 2020-06-10

### Changed
- Transform model by dx = 8.96, dy = 0.00, dz = -11.45 (H-point is now 0, 0, 0)
- Update Section and Hourglass control for cortical bone shell elements
- Update density of lung cavity
- Release nodes pasted in the cervical spine articular processes tie-contacts

## 0.1.0 - 2020-04-30

### Added
- Vulnerable Road User (Standing) Model
- Hip joint capsule ligaments
- Teres ligament: Ligaments connecting the acetabulum with the femur head (at fovea capitis)
- Sacroiliac joint
- Interosseus membranes, connecting tibia and fibula
- Knee ligaments
- Patella Tendon
- Quadriceps Femoris
- Ankle Joints, including talus and calcaneus
- Wrist joints and radioulnar joints
- Coordinate systems according to ISB recommendations to describe joint angles (Wu et al., 2002; Wu et al., 2005; Wu & Cavanagh, 1995)
- Body region-wise node numbering

### Changed
- Keyword file structure
  - Include files
  - `common` directory for includes common to all models
- Pelvis Position
- Soft tissue mesh improvement
  - Pelvic region
  - Ankle joint
  - Hand
  - Internal organs 'blob'
- Improve mesh quality in femur, tibia
- Reposition Scapula
- Improve sternum mesh
- Update PIDs to VIVA+ nomenclature
  - Neck Muscles
  - Thoracic and Lumbar Spine
  - Lower Extremity and Pelvis
  - Soft tissues (below neck)
  - Upper extremity and Shoulder
  - Ribcage

### Removed
- Kinematic joints in the hip joint and knee joint  

## 0.0.1 - 2020-01-31

### Added
- Preliminary seate 50F model
