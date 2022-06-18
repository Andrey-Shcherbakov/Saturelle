# Saturelle
Projet 1A Ecole Polytechnique

sujet proposé par Katia Meziani
meziani@ceremade.dauphine.fr
1 Questions préliminaires
Soit N = {1, · · · , n} ou n ∈ N∗. On se place dans le plan euclidien canonique R
2 et on choisit un couple
(p, q) ∈ N
2
∗
. On appellera chemin une suite de points (Mk)k=1,··· ,n à coordonnées entières telle que pour
tout k ∈ {1, · · · , n},
−−−−−−→ MkMk+1 ∈ {−→i ,
−→j }. On s’intéresse aux chemins joignant l’origine O au point de
coordonnées (p, q). 
T1. Dénombrer le nombre de chemins possibles joignant l’origine O au point (p, q).
T2. n suppose que q > p. On cherche à dénombrer le nombre de chemins joignant l’origine au point
(p, q) en restant toujours strictement au-dessus de la première bissectrice (sauf en l’origine bien sûr).
Montrer que le nombre de chemins joignant (0, 1) au point (p, q) et coupant la première bissectrice est
égal au nombre de chemins joignant (1, 0) au point (p, q).
T3. On choisit au hasard (de façon équiprobable) un chemin joignant l’origine au point (p, q), calculer
la probabilité que ce chemin ne coupe pas la première bissectrice (sauf en l’origine).
T4. On suppose maintenant que q ≥ p. On choisit au hasard (de façon équiprobable) un chemin
joignant l’origine au point (p, q). Calculer la probabilité que ce chemin ne traverse pas la première
bissectrice.
S1. Écrire un programme qui prend en entrée un couple (p, q) avec p ≤ q et qui renvoie un tableau
numpy de taille p+q qui code un chemin de (0, 0) à (p, q) uniforme parmi tous les chemins possibles. On
pourra d’abord coder une fonction qui code (par convention) Nord=1 et Est=0 dans le tableau numpy.
Indication: on pourra utiliser la méthode np.random.permutation pour générer une permutation
aléatoire uniforme.
S2. Vérifier la validité du code précédent en écrivant un code Python qui affiche 5 chemins aléatoire
de (0,0) à (p, q). On affichera un graphique pour (p = 10, q = 10), un autre pour (p = 100, q = 150) et un
dernier pour (p = 1000, q = 1000). Que constatez-vous, pouvez-vous l’expliquer (informellement) ?
S3. Implémenter une fonction qui prend en entrée un couple (p, q) avec p ≤ q et qui renvoie un
chemin de (0,0) à (p, q) qui ne traverse pas la première bissectrice en utilisant la méthode du rejet
(qui consiste à générer des chemins avec le code S1 et à conserver le premier qui ne traverse pas la
première bissectrice). Justifier rapidement que cette algorithme de rejet renvoie bien un chemin qui suit
la mesure uniforme sur les chemins qui ne traversent pas la première bissectrice.
S4. Reprendre la question S2 avec des chemins qui ne traversent pas la première bissectrice.
S5. Notons R le nombre de rejets réalisés lors de la génération d’un chemin qui ne traverse pas la
première bissectrice selon l’algorithme implémenté en S3. D’après la question T4, quelle est la loi de
R ? Vérifier numériquement ce résultat en générant un grand nombre de tels chemin et en affichant
l’histogramme de la loi empirique de R que l’on superposera avec la loi théorique. On affichera les
résultats pour (p = 10, q = 10) puis pour (p = 20, q = 40).
2 Déplacement de la sauterelle sur une ligne
On peut reprendre les résultats de la partie précédente pour résoudre cette partie. On imagine une
sauterelle, se déplaçant sur les entiers relatifs partant de l’origine et se déplaçant d’un pas à gauche ou
à droite de façon équiprobable.
T5. Quelle est la probabilité Pn que la sauterelle revienne à l’origine en 2n étapes ?
T6. En réinterprétant les chemins de l’exercice précédent, calculer la probabilité que la sauterelle
revienne à l’origine pour la première fois en 2n étapes.
61
T7. Modélisons la marche aléatoire de la sauterelle avec des variables aléatoires. Soient (Xn) des
variables aléatoires indépendantes de même loi avec
P(Xn = 1) = P(Xn = −1) = 1
2
.
Notons S0 = 0 et Sn = S0 +
Pn
k=1 Xk la position de la sauterelle à la n-ième étape. Expliquer pourquoi
la probabilité P{∀i ≥ n + 1, Pi
k=n+1 Xk 6= 0} ne dépend pas de n.
T8. Déterminer un équivalent de
Pn = P(S2n = 0)
lorsque n tend vers +∞ et étudier la nature de la série P
n≥0 Pn.
T9. Montrer que la probabilité pour que la sauterelle ne passe qu’un nombre fini de fois par l’origine
est donnée par la somme
X
n≥0
P
(
S2n = 0 et
∀i ≥ 2n + 1, X
i
k=2n+1
Xk 6= 0!) .
T10. Calculer pour tout n ∈ N
P

∀i ≥ 2n + 1, X
i
k=2n+1
Xk 6= 0!
et en déduire que la sauterelle retourne presque sûrement une infinité de fois à l’origine.
T11. Que penser de la somme
X
n≥1
1
2
2n−1
1
2n − 1
C
n
2n−1
?
S6. Créer un programme en Python qui trace sur un même graphique 5 réalisations de (n, Sn(ω)) sur
l’intervalle [0, 1000].
S7. En simulant un grand nombre de marches, tracer la fonction de répartition empirique du premier
temps de retour en 0 de la sauterelle. On superposera sur le même graphique la fonction de répartition
théorique que l’on calculera numériquement à l’aide de la formule obtenue en T6.
3 Déplacement de la sauterelle en dimension 2
On s’intéresse maintenant au saut d’une sauterelle à partir de l’origine mais se déplaçant dans Z
2
.
Soient Dn = (Xn, Yn) des vecteurs aléatoires indépendants de même loi avec
P(Dn = (1, 0)) = P(Dn = (−1, 0)) = P(Dn = (0, 1)) = P(Dn = (0, −1)) = 1
4
.
T12. Les variables Xn et Yn sont-elles indépendantes? On pose Un = Xn + Yn et Vn = Xn − Yn. Les
variables Un et Vn sont-elles indépendantes?
62
T13. Notons S0 = (0, 0) et Sn = S0 +
Pn
k=1 Dk ∈ Z
2
la position de la sauterelle à l’instant n. Montrer
que
E (kSnk2) ≤
√
n
où k · k2 dénote la norme euclidienne.
T14. Calculer la probabilité que la sauterelle revienne presque sûrement une infinité de fois à l’origine.
S8. Créer un programme en Python qui trace sur un même graphique 4 réalisations (n, Sn(ω)) sur
l’intervalle [0, 1000]. On pourra utiliser la librairie mpl_toolkits1 pour réaliser les graphiques 3D.
