flowchart TD
%% Nodes
    ARTINT("Article")
    ADRESSE("Adresse")
    OFRDOSSIER("Dossier")
    OFR("Offre")
    CDE("Commande client")
    CDEPOS("Affaire")
    CDEPLANLIV("Plan de livraison")
    CDEBULL("Buletin de livraison")
    ARTCLT("Article client")
    PCEJRNl("Mouvement stock pièces")
    ARTGAMME("Gamme article")
    ARTGAMMETYPE("Gamme type")
    ARTINTGAMME("Gamme article")
    ARTCOMPOS("Composant article")
    ACHDEMANDE("Demande d'achat")
    ACHDEMANDEPOS("Position de la demande")
    DIVCDE("Commande stock")
    DIVCDEPOS("Position de la commande stock")
    MATCDETOP("Commande matière groupée")
    MATCDE("Commande matière")
    MATCDEPOS("Position de commande matière")
    MATJRNL("Mouvement matière")
    MATSTOCK("Fiche stock matière")
    MATTBL("Type matière")
    MATFOURN("Fournisseur matière")
    CDEOF("Ordre de fabrication")
    CDEOP("Opération de l'ordre de fabrication")
    CDEMACHOP("Type de machine pour l'opération")
    SVIJRNL("Suivi")
    CDELOT("Lot OF")
    MCHTYPE("Type machine")
    MCH("Machine")
    ENCDEPART("Département")
    QALNCONF("NC")
    FACENTETE("Facture")
    FACLIGNE("Ligne facture")
    ARTMAT("Matière d'un article")

%% Edge connections between nodes
    OFR -- UNIKOFRDOSSIER --> OFRDOSSIER
    OFRDOSSIER -- NOCLT --> ADRESSE
    OFR -- UNIKARTINT --> ARTINT
    FACLIGNE -- NOFACTURE -->FACENTETE
    FACENTETE -- REFCLIENT -->ADRESSE
    FACLIGNE -- UNIKCDEJRNL --> CDEJRNL
    CDEJRNL -- NOCDEPOS --> CDEPOS
    CDEPOS -- NOCDEINT --> CDE
    CDE -- NOCLIENT --> ADRESSE
    CDEPLANLIV -- CDEPLANLIV --> CDEPOS
    CDEPOS -- UNIKARTINT --> ARTINT
    QALNCONF -- NOCLIENT --> ADRESSE
    QALNCONF -- UNIKARTINT -->ARTINT
    QALNCONF -- NOLOTLIVR --> CDEJRNL
    CDEJRNL -- NOCDEBULL --> CDEBULL
    CDEBULL -- NOCLIENT --> ADRESSE
    ARTCLT -- UNIKARTINT--> ARTINT
    ARTCLT -- NOCLIENT--> ADRESSE
    PCEJRNl -- UNIKARTINT -->ARTINT
    ARTGAMME -- UNIKGAMMETYPE --> ARTINT
    ARTGAMME -- UNIKGAMMETYPE --> GAMMETYPE
    ARTINTGAMME -- UNIKGAMMETYPE --> GAMMETYPE
    ARTINTGAMME -- UNIKARTINT --> ARTINT
    ACHDEMANDEPOS -- unikachdemande --> ACHDEMANDE
    ACHDEMANDEPOS -- UNIKARTINT --> ARTINT
    DIVCDEPOS -- unikdivcde --> DIVCDE
    DIVCDE -- NOFOURN --> ADRESSE
    DIVCDEPOS -- UNIKARTINT --> ARTINT
    MATJRNL --MATJRNL --> MATCDEPOS
    MATCDEPOS -- UNIKMATCDE --> MATCDE
    MATCDE -- UNIKMATCDETOP --> MATCDETOP
    MATCDETOP -- NOFOURN --> ADRESSE
    MATJRNL --UNIKMATSTOCK -->MATSTOCK
    MATSTOCK -- CODEMATINT -->MATTBL
    MATFOURN -- NOREFADRES --> ADRESSE
    MATFOURN -- UNIKMATSTOCK --> MATSTOCK
    ARTMAT -- UNIKMATSTOCK --> MATSTOCK
    ARTMAT -- UNIKARTINT --> ARTINT
    SVIJRNL --UNIKCDEOP --> CDEOP
    CDEOP -- UNIKCDEOF --> CDEOF
    CDEOF -- UNIKARTINT --> ARTINT
    CDEMACHOP -- MACHTYPE -->MCHTYPE
    CDEMACHOP -- UNIKCDEOP -->CDEOP
    CDEOP -- NOMACH --> MCH
    MCH -- DEPART -->ENCDEPART
    SVIJRNL -- NOMACH --> MCH
    MCH -- MACHTYPE -->MCHTYPE
    CDELOT -- UNIKCDEOF --> CDEOF