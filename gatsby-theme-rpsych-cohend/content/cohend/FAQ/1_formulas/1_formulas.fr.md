---
title: Quelles sont les formules ?
order: 1
---

### *d* de Cohen
Le *d* de Cohen est simplement la différence standardisée des moyennes,

$$ \delta = \frac{\mu_2-\mu_1}{\sigma}$$,

où $\delta$ est le paramètre de population du *d* de Cohen. Il est supposé que que $\sigma_1=\sigma_2=\sigma$, c'est-à-dire que les variances des populations sont homogènes. Enfin, $\mu_i$ est la moyenne respective de chaque population.

### Le U<sub>3</sub> de Cohen
Cohen (1977) a défini le U<sub>3</sub> comme la mesure du non-chevauchement, lorsque "l'on prend le pourcentage de la population A qui est inférieure à la moitié supérieure de la population B". Le *d* de Cohen peut être converti en U<sub>3</sub> de Cohen en utilisant la formule suivante

$$U_3 = \Phi(\delta)$$

où $\Phi$ est la distribution de répartition (ou fonction de distribution cumulative) de la distribution normale standard, et $\delta$ la population du *d* de Cohen.

### Overlap
Généralement appelé coefficient de chevauchement (overlapping coefficient (OVL) en anglais). Le *d* de Cohen peut être converti en OVL en utilisant la formule suivante (Reiser et Faraggi, 1999)

$$\text{OVL}=2\Phi(-|\delta|/2) $$

où $\Phi$ est la distribution de répartition de la distribution normale standard, et $\delta$ la population du *d* de Cohen.

### Probabilité de supériorité
C'est la taille d'effet, avec de nombreux noms : taille d'effet en langage commun (LC), aire sous la fonction d'efficacité du récepteur (AUC), ou simplement A pour ces versions non-paramétriques (Ruscio et Mullen, 2012). Il se veut plus intuitif pour les personnes sans aucune formation statistique. La taille de l'effet donne la probabilité qu'une personne choisie au hasard dans le groupe traitement ait un score plus élevé qu'une personne prise au hasard dans le groupe contrôle. Le *d* de Cohen peut être converti en LC en utilisant la formule suivante :

$$\text{CL}=\Phi\left(\frac{\delta}{\sqrt{2}}\right)$$

où $\Phi$ est la distribution de répartition de la distribution normale standard, et $\delta$ la population du *d* de Cohen.

### Number Needed to Treat
NNT est le nombre de patients que nous devrions traiter pour atteindre un résultat plus favorable comparé au groupe contrôle. Furukawa et Leucht (2011) donnent la formule suivante pour convertir le *d* de Cohen en NNT :

$$ \text{NNT} = \frac{1}{  \Phi(\delta + \Psi(CER))-CER}$$

où $\Phi$ est la distribution de répartition de la distribution normale standard et $\Psi$ son inverse, CER est le ratio d'évènement en condition contrôle et $\delta$ la population du *d* de Cohen. **N.B. CER est fixé à 20 % dans la visualisation ci-dessus. Vous pouvez changer cette valeur grâce au bouton paramètres à droite du Slider**. Les définitions d'un "évènement" ou d'une "réponse" sont arbitraires et doivent être définies comme la proportion de patients qui sont en rémission, c'est-à-dire inférieure à un seuil défini par un questionnaire standardisé. Il est possible de convertir le *d* de Cohen en une version du NNT qui ne prend pas en compte le ratio d'évènement du groupe contrôle. Le lecteur interessé doit regarder la publication de Furukawa et Leucht (2011) qui donne un argument convaincant et montre pourquoi cela complique l'interprétation du NNT.

### Code R pour calculer le NNT depuis le *d* de Cohen
Puisque j'ai reçu beaucoup de demandes à propos du code R pour la formule ci-dessus, le voici :

```r
CER <- 0.2
d <- 0.2
1 / (pnorm(d + qnorm(CER))-CER)
```

### Références

* Baguley, T. (2009). Standardized or simple effect size: what should be reported? *British journal of psychology*, 100(Pt 3), 603–17.
* Cohen, J. (1977). *Statistical power analysis for the behavioral sciencies*. Routledge.
* Furukawa, T. A., & Leucht, S. (2011). How to obtain NNT from Cohen's d: comparison of two methods. *PloS one*, 6(4).
* Reiser, B., & Faraggi, D. (1999). Confidence intervals for the overlapping coefficient: the normal equal variance case. *Journal of the Royal Statistical Society*, 48(3), 413-418.
* Ruscio, J. (2008). A probability-based measure of effect size: robustness to base rates and other factors. *Psychological methods*, 13(1), 19–30.
* Ruscio, J., & Mullen, T. (2012). Confidence Intervals for the Probability of Superiority Effect Size Measure and the Area Under a Receiver Operating Characteristic Curve. *Multivariate Behavioral Research*, 47(2), 201–223.
