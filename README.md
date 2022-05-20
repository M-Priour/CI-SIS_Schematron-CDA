# CI-SIS - Liste des Schematrons CDA de l'Espace de tests
#### Contenu du répertoire ####
Vous trouverez dans ce repository l'ensembles des schematrons pour les CDA du CI-SIS  utilisés par l'[Espace de tests](https://interop.esante.gouv.fr/EVSClient/cda/validator.seam?standard=CDA-ASIP&extension=ASIP) :
- ANS-ANEST-CR-ANEST_2021.01
- ANS-ANEST-CR-CPA_2021.01
- ANS-AVC-AUNV_2019
- ANS-AVC-EUNV_2019 
- ANS-AVC-PAVC_2019
- ANS-AVC-SUNV_2019
- ANS-CANCER-CR-GM_2021.01
- ANS-CANCER-D2LM-FIDD_2021.01
- ANS-CANCER-D2LM-FIN_2021.01
- ANS-CANCER-FRCP-2021.01
- ANS-CANCER-PPS_2021.01
- ANS-CR-BIO-2021.01
- ANS-CSE-CS24_2021.01
- ANS-CSE-CS8_2021.01
- ANS-CSE-CS9_2021.01
- ANS-DLU-DLU_2021.01
- ANS-DLU-FLUDR_2021.01
- ANS-DLU-FLUDT_2021.01
- ANS-LDL-EES_2020.01
- ANS-LDL-SES_2020.01
- ANS-OBP-SAP_2021.01
- ANS-OBP-SCE_2021.01
- ANS-OBP-SCM_2021.01
- ANS-OPH-BRE_2021.01
- ANS-OPH-CR-RTN_2021.01
- ANS-Structuration minimale des documents de sante v2.9
- ANS-TLM_CR_2021.01
- ANS-TLM_DA_2021.01
- ANS-VAC-2021.01
- ANS-VAC-NOTE 2021.01
- ANS-VSM_2013 (v1.4)


#### Exploitation ####
Pour pouvoir exploiter, ces schematrons qui sont directement issus de l'outil de spécification (Art-Decor). 
Nous vous invitions à utiliser la librairie ph-schematron :
 -  https://github.com/phax/ph-schematron/

Cette librairie offre une implementation native en java pour la validation. 
Les performances observés permettent de valider un CR-BIO en quelques secondes.

#### Exemple de code avec ph-schematron ####

//Initialisation du schematron et du document CDA à valider
String fileShematron = "xxxxxx";
File fileDocumentCda = new File("xxxxxxx");

//Chargement du schematron
ISchematronResource aResPure;
aResPure = SchematronResourceSCH.fromFile (fileShematron);
 if(!aResPure.isValidSchematron ())
     throw new IllegalArgumentException ("Invalid Schematron!");
     
 //Validation du schematron et récupération du résulat    
 final Document aDoc =  aResPure.applySchematronValidation (new StreamSource (fileDocumentCda)); 


#### Retouver le bon validateur ou schematron pour valider le document CDA ####
Pour pouvoir identifier, le bon validateur vous pouvez vous appuyer sur la balise "templateId" du document CDA.





