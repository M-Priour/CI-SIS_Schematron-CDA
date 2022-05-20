# CI-SIS - Liste des Schematrons CDA de l'Espace de tests
## Contenu du répertoire
Vous trouverez dans ce repository l'ensembles des schematrons pour les CDA du CI-SIS  utilisés par l'[Espace de tests](https://interop.esante.gouv.fr/EVSClient/cda/validator.seam?standard=CDA-ASIP&extension=ASIP) :
Les schematrons ci-dessous sont directement issus de l'outil de spécification (Art-Decor) : 
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


## Exploitation 
Pour pouvoir exploiter, nous vous invitions à utiliser la librairie ph-schematron :
 -  https://github.com/phax/ph-schematron/

Cette librairie offre une implementation native en java pour faire de la validation via des schématrons. 
Les performances observés permettent de valider un CR-BIO en quelques secondes.

### Utilisation de ph-schematron 
`Exemple de code :`

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


### Identififier le bon validateur ou schematron pour valider le document CDA
Pour pouvoir identifier, le bon validateur vous pouvez vous appuyer sur l'attribut `root`  balise `templateId` du document CDA.


`Exemple d'un document CDA:`

    <ClinicalDocument xmlns="urn:hl7-org:v3" xmlns:lab="urn:oid:1.3.6.1.4.1.19376.1.3.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >
     <realmCode code="FR" />
     <typeId root="2.16.840.1.113883.1.3" extension="POCD_HD000040" />
     <!-- Déclarations de conformité HL7 France -->
     <templateId root="2.16.840.1.113883.2.8.2.1" />
     <!-- Déclarations de conformité CI-SIS -->
     <templateId root="1.2.250.1.213.1.1.1.1" />
     <!-- Déclarations de conformité au modèle CR-BIO du CI-SIS -->
     <templateId root="1.3.6.1.4.1.19376.1.3.3" extension="2021.01" />


Dans l'exemple ci desssus, c'est le schematron `ANS-CR-BIO-2021.01` qui permettera de valider le document.


`Vous touverez ci-dessous le mapping entre les  templateId et les  schématrons` :

    1.2.250.1.213.1.1.1.40=ANS-ANEST-CR-ANEST_2021.01
    1.2.250.1.213.1.1.1.41=ANS-ANEST-CR-CPA_2021.01
    1.2.250.1.213.1.1.1.15=ANS-AVC-AUNV_2019
    1.2.250.1.213.1.1.1.16=ANS-AVC-EUNV_2019 
    1.2.250.1.213.1.1.1.25=ANS-AVC-PAVC_2019
    1.2.250.1.213.1.1.1.17=ANS-AVC-SUNV_2019
    1.2.250.1.213.1.1.1.32=ANS-CANCER-CR-GM_2021.01
    1.2.250.1.213.1.1.1.28=ANS-CANCER-D2LM-FIDD_2021.01
    1.2.250.1.213.1.1.1.27=ANS-CANCER-D2LM-FIN_2021.01
    1.2.250.1.213.1.1.1.8=ANS-CANCER-FRCP-2021.01
    1.2.250.1.213.1.1.1.26=ANS-CANCER-PPS_2021.01
    1.3.6.1.4.1.19376.1.3.3=ANS-CR-BIO-2021.01
    1.2.250.1.213.1.1.1.5.3=ANS-CSE-CS24_2021.01
    1.2.250.1.213.1.1.1.5.1=ANS-CSE-CS8_2021.01
    1.2.250.1.213.1.1.1.5.2=ANS-CSE-CS9_2021.01
    1.2.250.1.213.1.1.1.22=ANS-DLU-DLU_2021.01
    1.2.250.1.213.1.1.1.24=ANS-DLU-FLUDR_2021.01
    1.2.250.1.213.1.1.1.23=ANS-DLU-FLUDT_2021.01
    1.2.250.1.213.1.1.1.21=ANS-LDL-EES_2020.01
    1.2.250.1.213.1.1.1.29=ANS-LDL-SES_2020.01
    1.2.250.1.213.1.1.1.12.1=ANS-OBP-SAP_2021.01
    1.2.250.1.213.1.1.1.12.5=ANS-OBP-SCE_2021.01
    1.2.250.1.213.1.1.1.12.4=ANS-OBP-SCM_2021.01
    1.2.250.1.213.1.1.1.12.3=ANS-OBP-SNE-2021.01
    1.2.250.1.213.1.1.1.12.2=ANS-OBP-SNM-2021.01
    1.2.250.1.213.1.1.9=ANS-OPH-BRE_2021.01
    1.2.250.1.213.1.1.1.18=ANS-OPH-CR-RTN_2021.01
    1.2.250.1.213.1.1.1.20=ANS-PPS-PAERPA_2021.01 
    1.2.250.1.213.1.1.1.30=ANS-SDM-MR-2021.01
    1.2.250.1.213.1.1.1.38=ANS-TLM_DA_2021.01
    1.2.250.1.213.1.1.1.37=ANS-VAC-2021.01
    1.2.250.1.213.1.1.1.46=ANS-VAC-NOTE 2021.01
    1.2.250.1.213.1.1.1.13=ANS-VSM_2013 (v1.4)

