==============================================================

  INCIDENTS: INCidence Independent DEcomposition of NeTworkS

==============================================================

MATLAB was used to develop the function used here.
The function incidenceIndepDecomp returns the finest nontrivial incidence independent decomposition of a chemical reaction network (CRN), if it exists. If no such decomposition exists, a message appears saying so. Furthermore, the output variables 'model', 'I_a', 'G', and 'P' allows the user to  view the following, respectively:

   - Complete network with all the species listed in the 'species' field of the structure 'model'
   - Incidence matrix of the network
   - Undirected graph of I_a
   - Partitions representing the decomposition of the reactions



=================================
How to fill out 'model' structure
=================================

'model' is the input for the function incidenceIndepDecomp. It is a structure, representing the CRN, with the following fields (the kinetics of the network is not needed):

   - id: name of the model
   - species: a list of all species in the network; this is left blank since incorporated into the function is a step which compiles all species used in the model
   - reaction: a list of all reactions in the network, each with the following subfields:
        - id: a string representing the reaction
        - reactant: has the following further subfields:
             - species: a list of strings representing the species in the reactant complex
             - stoichiometry: a list of numbers representing the stoichiometric coefficient of each species in the reactant complex (listed in the same order of the species)
        - product: has the following further subfields:
             - species: a list of strings representing the species in the product complex
             - stoichiometry: a list of numbers representing the stoichiometric coefficient of each species in the product complex (listed in the same order of the species)
        - reversible: has the value true or false indicating if the reaction is reversible or not, respectively

To fill out the 'model' structure, write a string for 'model.id': this is just to put a name to the network. To add the reactions to the network, use the function addReaction where the output is 'model'. addReaction is developed to make the input of reactions of the CRN easier than the input in [5]:

   addReaction
      - OUTPUT: Returns a structure called 'model' with added field 'reaction' with subfields 'id', 'reactant', 'product', 'reversible', and 'kinetic'. The output variable 'model' allows the user to view the network with the added reaction.
      - INPUTS
           - model: a structure, representing the CRN
           - id: visual representation of the reaction, e.g., reactant -> product (string)
           - reactant_species: species of the reactant complex (cell)
           - reactant_stoichiometry: stoichiometry of the species of the reactant complex (cell)
           - reactant_kinetic: kinetic orders of the species of the reactant complex (array)
           - product_species: species of the product complex (cell)
           - product_stoichiometry: stoichiometry of the species of the product complex (cell)
           - product_kinetic: "kinetic orders" of the species of the product complex, if the reaction is reversible (array); if the reaction in NOT reversible, leave blank
           - reversible: logical; whether the reaction is reversible or not (true or false)
      * Make sure the function addReaction is in the same folder/path being used as the current working directory.



========
Examples
========

9 examples are included in this folder:

   - Example 1: A simple network [1]

   - Example 2: Baccam influenza virus model [1]

   - Example 3: Baccam influenza virus model with delayed virus production [1]

   - Example 4: Figure 7 [6]

   - Example 5: Insulin metabolic signaling network [3]

   - Example 6: Insulin resistance model [4]

   - Example 7: Schmitz Wnt signaling network [2]

   - Example 8: Feinberg augmented Lee Wnt signaling network [2]

   - Example 9: MacLean Wnt signaling network [2]



===================
Contact Information
===================

For questions, comments, and suggestions, feel free to contact me at pvnlubenia@yahoo.co.uk.


- Patrick Lubenia (13 June 2024)



==========
References
==========

   [1] Hernandez B, Amistas D, De la Cruz R, Fontanil L, de los Reyes V A, Mendoza E (2022) Independent, incidence independent and weakly reversible decompositions of chemical reaction networks. MATCH Commun Math Comput Chem, 87(2):367--396. https://doi.org/10.46793/match.87-2.367H

   [2] Hernandez B, Lubenia P, Mendoza E (2024) Embedding-based comparison of reaction networks of Wnt signaling. MATCH Commun Math Comput Chem (in press)

   [3] Lubenia P, Mendoza E, Lao A (2022) Reaction network analysis of metabolic insulin signaling. Bull Math Biol, 84(129):1Ð12. https://doi.org/10.1007/s11538-022-01087-3

   [4] Lubenia P, Mendoza E, Lao A (2024) Comparative analysis of kinetic realizations of insulin signaling. J Theor Biol, 577:1Ð12. https://doi.org/10.1016/j.jtbi.2023.111672

   [5] Soranzo N, Altafini C (2009) ERNEST: a toolbox for chemical reaction network theory. Bioinform 25(21):2853-2854. https://doi.org/10.1093/bioinformatics/btp513

   [6] Yu P, Craciun G (2018) Mathematical analysis of chemical reaction systems. Isr J Chem 58:1-10. https://doi.org/10.1002/ijch.201800003