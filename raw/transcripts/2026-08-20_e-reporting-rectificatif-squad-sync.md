août 20, 2026
E-reporting rectificatif - squad sync - Transcription
00:00:00

Ludovic Lelievre: un reporting de cette même période et du même type qui est transmis et par parce que au moment où
Audric Podmilsak: Bah ou même ou même accepter qui est transmis ou même
Ludovic Lelievre: tu où tuenvoies Oui.
Paul Sorrentino: H
Ludovic Lelievre: Oui.
Audric Podmilsak: accepter.
Ludovic Lelievre: à partir du transmis mais tu maisort au moment où tu
Audric Podmilsak: Ouais.
Ludovic Lelievre: t'envoies ton reporting rectificatif s'il y a s'il en avait un qui était déjà transmis ou accepté dans la période, il passe en annulé. Il passera en annulé. Du coup, lui c'est un annulé remplace pour cette période donc c'est le c'est le
Audric Podmilsak: Euh ah oui d'accord. OK. Donc l'initial l'initial pass en annulé en ou en ou en rectifié plutôt pour être précis,
Ludovic Lelievre: rectif. Ouais ouais
Audric Podmilsak: il passe en rectifié et il a un lien vers son rectificatif. Donc tuas un lien entre les deux et tu sais faire leif. Et ce que tu dis c'est que si tu refais un 3è rectificatif derrière enfin un 3è reporting


00:00:40

Ludovic Lelievre: ouais
Audric Podmilsak: qui rectifie le 2è celui-là il a un lien sur celui d'avant à chaque fois tu mis sur un
Ludovic Lelievre: exactement exactement exactement.
Audric Podmilsak: OK
Fabien Riou: M.
Ludovic Lelievre: C'est le c'est le dernier qui est transmis à l'administration fiscale qui fait foi comme étant euh la base de la source de vérité de ce que les que l'administration fiscale a comme
Audric Podmilsak: et il est complet à il est complet à chaque fois c'est comme les impôts en
Ludovic Lelievre: information. Ouais.
Audric Podmilsak: fait OK d'accord
Ludovic Lelievre: Et il écrase il écrase la veille celui d'avant. Donc c'est pour ça que c'est dur de parler de initial. Peut-être parler de reporting précédent.
Audric Podmilsak: H ouais pourquoi il y a pas en fait il y a pas besoin de de En fait un rectificatif cible forcément une période de reporting. Tu as une période de reporting rectificative qui cible une période de
Ludovic Lelievre: Ouais.
Audric Podmilsak: reporting.
Ludovic Lelievre: Transmis.
Audric Podmilsak: Bah il faut effectivement faut qu'il soit qui est transmis ou pas parce que tu peux aussi en avoir qui non l'ont pas


00:01:33

Ludovic Lelievre: Oui. Qui n'en ont pas. Oui. Oui, exactement.
Audric Podmilsak: puisque donc il aura c'est si jamais ça a jamais été transmis donc il y a ces deux cas d'usage donc
Ludovic Lelievre: Ouais.
Fabien Riou: Ouais.
Audric Podmilsak: ok faut bien cibler donc les deux cas possibles dans voilà soit tu cibles une période qui a déjà été
Fabien Riou: ou non existant quoi.
Audric Podmilsak: traitée et tu fais un créatif dessus soit tu cibles une période absente qui qu' a un oubli et tu fais unif dessus et après tu réflétif tu peux toujours en faire autant que tu veux et tu pointes sur une autre période.
Paul Sorrentino: M.
Audric Podmilsak: OK donc c'est du 01 là-dessus.
Fabien Riou: Hm.
Audric Podmilsak: OK,
Ludovic Lelievre: Oui.
Audric Podmilsak: mais le mécanique la mécanique reste la même. C'estàdire que tu as on va générer un FRR complet, on va l'envoyer à CGDIM, il nous envoie un ID transmission et à partir de cet ID là,
Ludovic Lelievre: Oui.
Audric Podmilsak: on aura la nouvelle point qui permet de l'envoyer à DGF et ça quoi.


00:02:11

Ludovic Lelievre: Oui, c'est ça.
Audric Podmilsak: Et avec ça, on pourra faire le hack dessus si c'est accepté ou pas quoi.
Ludovic Lelievre: Ouais.
Audric Podmilsak: OK.
Fabien Riou: Eh
Audric Podmilsak: Mais tu vois, c'est pour ça en fait que moi voyant tout ça, j'ai l'impression que la stratégie d'y aller de bout en bout sur le truc AP est plus
Fabien Riou: Eh
Audric Podmilsak: simple parce qu'en fait là déjà toutes ces règles là, il va falloir qu'on les pense, qu'on les digère et après on se dira OK bon ben dans le cas des autres types,
Ludovic Lelievre: Ouais.
Audric Podmilsak: le B2C, le machin, comment est-ce qu'on rentre dans tel ou tel truc? Parce qu'on aura assez d'emmerde aussi. Ça ça va pas être si simple à chaque fois parce que des fois on fait on fait des checks sur les doublons, des conneries comme ça mais euh j'ai l'impression que c'est plus simple de rentrer de bout en bout sur on
Fabien Riou: Mais j'avais juste une question,
Audric Podmilsak: pourra Non
Fabien Riou: je me posais la question.


00:02:51

Fabien Riou: AP ils utilisent la note public API? Non ils ont direct.
Audric Podmilsak: non ils ont un lien direct sur nous en fait c'est pour Yeah.
Paul Sorrentino: M.
Audric Podmilsak: aussi chez AP et ils ont eux ils nous envoient soit euh un poste pour la création initiale, soit un put quand il modifie quelque chose, soit un delite. Et ça indépendamment adapte pour l'instant nous dans tous les cas, on accepte tout leur flux.
Fabien Riou: OK.
Audric Podmilsak: C'est juste que tous ceux qui sont hors période pour l'instant on les rejette basta.
Fabien Riou: OK.
Audric Podmilsak: On les rejette en rouge en disant c'est hors période ce qui à terme n'est plus juste puisque du coup tu peux tu peux toujours te tromper et
Fabien Riou: D'accord.
Audric Podmilsak: corriger un truc. Donc à terre se branche làdessus
Fabien Riou: Donc la modification, on a les données de modification,
Audric Podmilsak: et
Fabien Riou: de suppression, on a on a tout ça quoi. On reçoit ça.
Audric Podmilsak: ouais bah techniquement on avec eux sera plus facile parce que soit ce sera des postes et donc du coup on pourra dire"Ah tiens c'est un poste donc c'est une création alors que je suis hors période donc on sait qu'on a'ura pas de période rectificative euh


00:03:36

Fabien Riou: OK.
Audric Podmilsak: enfin faut voir comment est-ce qu'on on le code.
Fabien Riou: OK.
Audric Podmilsak: On peut dire de faire soit comme ça soit de chercher une période de transmission comme tu l'as proposé avant dans la dans la step 2.
Fabien Riou: OK.
Audric Podmilsak: Je pense ça ce sera à voir au cas par cas. Mais on aura moyen de trouver en fait euh dans tous les cas si une une facture est déjà là ou pas et si si elle est sur si elle est
Fabien Riou: OK.
Audric Podmilsak: rectificative ou
Fabien Riou: Alors,
Audric Podmilsak: pas.
Fabien Riou: je vais finir justement l'étape
Paul Sorrentino: Bah c'est pas parce que la facture existe pas qu'elle est pas rectificative
Fabien Riou: 5.
Paul Sorrentino: hein.
Audric Podmilsak: Bah si parce qu'en fait si elle est si elle est enfin non oui je suis d'accord mais c'est si elle existe pas et qu'elle est sur une période passée elle est
Paul Sorrentino: H ouais
Audric Podmilsak: rectificative.
Fabien Riou: Ouais. Euh mais ça changera pas le process actuel de toute façon.
Paul Sorrentino: exact.
Fabien Riou: C'est juste on va check, il y aura des checks en plus et le côté comparé comparé qui va qui va arriver en plus alors qu'aujourd'hui on compare pas quoi.


00:04:25

Fabien Riou: Euh OK. L'étape 5 juste du coup on a on a créé un rectificatif en fonction euh de la comparaison et de la comparaison et des différents états. On a créé un rectificatif. Euh il y a aussi l'étape 5. Le système vérifie est-ce que le reporting rectificatif est vide. Oui. Donc du coup bah si c'est vide euh du coup tout a été tout a été euh euh
Ludovic Lelievre: Ça c'est le même cas que le initial. Si on se retrouve avec un rectificatif vide où il a plus lieu d'être, on supprime
Fabien Riou: donc c'est déjà actuel
Audric Podmilsak: Oui. Bah après en fait tout dépend si on si on se base sur les mécaniques qu'on a actuellement pour une période de reporting. Moi je pense que c'est une bonne idée parce que ça reste une période de reporting. C'est juste qu'elle est qualifiée d'un d'une nouvelle façon. Euh mais oui, si si elle dès qu'elle est dès que la dernière truc est supprimée, ça vient euh ça vient nettoyer la


00:05:19

Fabien Riou: Alors si c'est si c'est vide ou alors si tout si tout est en
Paul Sorrentino: Ouais, mais
Ludovic Lelievre: H
Audric Podmilsak: ligne.
Fabien Riou: état inchangé quoi. Tout est revenu en état inchangé. Et ben du coup, on supprime également ce
Ludovic Lelievre: Ouais.
Audric Podmilsak: Ouais. Donc du coup,
Fabien Riou: rectificatif.
Audric Podmilsak: c'est un peu différent.
Ludovic Lelievre: Donc il y aurait en vision ces deux règles pour automatiser la suppression euh automatique d'un reporting rectificatif. Sachant que ça c'est la vision cible et on sait que on aura un end point de la part de CGIM pour supprimer un projet de rectification. Voilà, c'est c'est aussi la stratégie de comment est-ce qu'on commence d'abord en V1 par si tu veux supprimer un rectificatif, tu vas le faire manuellement et pour ensuite arriver à une vision cible où on arrive à tout faire en automatique en identifiant OK rectificatif videou ça supprime. On a un reporting rectificatif qui est revenu à l'état identique de ce de la période qui est déjà transmise.


00:06:19

Ludovic Lelievre: On le
Paul Sorrentino: Il y a plus le la possibilité d'ouvrir un rectificatif
Ludovic Lelievre: supprime.
Paul Sorrentino: manuellement
Audric Podmilsak: Comment ça si manuellement en créant
Fabien Riou: Non.
Paul Sorrentino: de dans quand on ouvre un reporting transmis. Fabien, tu avais pensé à un bouton en haut à droite ouvrir un
Fabien Riou: Ouais. Ouais, j'ai mais on a revu ça parce que l'utilisateur
Paul Sorrentino: rectificatif.
Fabien Riou: euh va pas se dire tiens, je je veux créer un rectificatif, je ce qu'il veut lui c'est supprimer cette facture, modifier cette facture ou ajouter cette facture. Et donc il va le faire dans son outil ERP dans AP ou alors dans de façon manuelle pour les transaction B2C ou les paiements B2C ou alors tout ce qui vient d'Ap il va pouvoir supprimer et donc automatiquement ça va créer ça va créer ça va créer un rectificatif en fonction de cette tâche là.
Paul Sorrentino: OK,
Fabien Riou: Pour ça je mettais en C'est pour ça que je le mettais à cette étape 4, la création et la suppression parce que on va voir,
Paul Sorrentino: c'est
Fabien Riou: on va réceptionner ce flux où on va actionner manuellement et du coup bah ça va ça va ça va décider en fonction de ça quoi, fonction de cette comparaison.


00:07:39

Fabien Riou: Je je propose un petit prototype comme ça on va pouvoir voir un peu
Audric Podmilsak: Juste avant tout petite question parce que là sur ce que tu as dit Ludo avant,
Fabien Riou: plus.
Audric Podmilsak: tu as parlé du endp de Cim mais en fait le end point de suppression c'est que si tu es trom que tu as tu as fait un correctif, tu l'as envoyé à Cim, tu t'es trompé et tu veux pouvoir le supprimer derrière.
Ludovic Lelievre: Non non,
Audric Podmilsak: C'est ça parce que parce qu'en fait nous
Ludovic Lelievre: c'est euh
Audric Podmilsak: c'est dire que c'est à quel moment que tu as besoin de supprimer un truc que tu envoies en fait parce
Ludovic Lelievre: Oui, il sera jamais envoyé.
Audric Podmilsak: que pour moi en fait quand on envoie voilà ça sert à rien en fait j'ai l'impression que ça sert à rien parce qu'en gros ce qui va se passer
Ludovic Lelievre: On pourrait le laisser. Ouais ouais
Audric Podmilsak: c'est que nous comme on fait pas les trucs automatiqu ce qui va se passer enfin à moins qu'on fasse des trucs automatiques mais j'ai je vous en ai pas parlé ici dans le


00:08:15

Paul Sorrentino: M.
Audric Podmilsak: flux c'està dire que le client il fait ses modifications il voit un rectificatif dedans il y a un bouton transmettre et il appuie dessus et
Ludovic Lelievre: non.
Audric Podmilsak: C'est là qu'on génère nous le FRR auprès de CGIM.
Ludovic Lelievre: Oui oui. OK.
Audric Podmilsak: Envoie une mission ID et c'est ça qu'on peut supprimer.
Ludovic Lelievre: Oui oui oui oui.
Audric Podmilsak: C'est ça. On peut prendre celle.
Ludovic Lelievre: Mais c'est vrai que si on a si on a rien envoyé à je dis il y a rien à supprimer.
Audric Podmilsak: Donc moi je enfin j'ai enfin bah présente-nous la maquette mais pour l'instant vous avez pas parlé de trucs automatiques. Donc euh
Ludovic Lelievre: Ah non non mais oui le mais le point de de Fabien là c'est qui est un peu différent
Audric Podmilsak: OK.
Ludovic Lelievre: de de ce qu'on avait présenté la dernière fois c'est quand on est dans un reporting transmis plutôt que d'ouvrir un reporting de dire je j'ouvre un reporting rectificatif et ensuite je fais mes actions.


00:09:03

Ludovic Lelievre: tu es dans le tu es dans le reporting transmis et là tu as les actions manuelles de sur les sur les
Audric Podmilsak: Ouais.
Ludovic Lelievre: transactions B2C, tu peux en ajouter, en modifier ou supprimer une facture de vente et c'est ça qui viendra créer le reporting rectificatif. Et donc on a tout au moment de la création d'un reporting rectificatif, il est obligatoirement différent de l'initial de du précédent parce qu'il y a toujours une action qui
Paul Sorrentino: H
Ludovic Lelievre: s'est passée pour cette création.
Paul Sorrentino: OK,
Ludovic Lelievre: Et du
Paul Sorrentino: j'ai un peu de mal à me projeter sur lui. Qu'est-ce qui qui aurait derrière avoir les maquettes
Fabien Riou: Et ben on va C'est une bonne transition. C'est une bonne transition.
Paul Sorrentino: ?
Fabien Riou: Euh j'ajoute également la création d'un rectificatif. à partir du moment où on a automatique à partir du moment aussi on a un rejet un rejet de CGD enfin de la DG FIP comme quoi il y a des choses à corriger et des choses qui vont pas donc du coup ça va aussi recréer un un rectificatif euh parce que la date du coup est est


00:09:59

Paul Sorrentino: M.
Audric Podmilsak: Pour pourquoi ça crée un régatif du coup?
Fabien Riou: passée et du coup
Audric Podmilsak: Mais avec tout qui est inchangé. C'est une règle à part parce que du coup tu es coincé parce qu'en fait si tu rectific tout qui est inchangé ça correspond pas avec ta règle ou quand tout est inchangé tu le
Fabien Riou: Non, c'est parce que du coup ça va rester en un changé avec des erreurs avec les erreurs de la DG
Audric Podmilsak: supprimes.
Fabien Riou: FIP sur euh sur les factures en question.
Audric Podmilsak: Ouais ben du coup ça marche pas parce que si tout tu as mis une règle avant tu as dit si tout est inchangé on le supprime.
Ludovic Lelievre: He.
Audric Podmilsak: Ce qui est logique puisque du coup c'est la même période que la période initiale.
Fabien Riou: Si tout est inchangé. Euh oui euh oui oui
Audric Podmilsak: C'était la règ que tu as donné avant.
Fabien Riou: bien. Attends.
Audric Podmilsak: En fait, j'ai l'impression que là, il vaut peut-être mieux juste afficher les erreurs dans la période courante et à partir de


00:10:51

Fabien Riou: Oui.
Audric Podmilsak: ces erreurslateur il va venir faire ses changements comme tu l'as dit avant à partir des factures.
Fabien Riou: Ouais. Non,
Audric Podmilsak: Pas bon.
Fabien Riou: il y aura peut-être un il y aura peut-être un deux état dans c là. peut-être un état euh un état rien et un état euh inchangé peut-être dans ces cas-là. Bon bref euh attends, je je présente un peu ça comme ça vous allez me dire
Audric Podmilsak: Vas-y.
Fabien Riou: euh donc là je suis dans la partie à transmettre.
Paul Sorrentino: M.
Fabien Riou: Euh je vais être un reporting facture d'achat. Quand je vais cliquer sur rectifier, je vais voir du coup on est dans un état rectifier et qu'est-ce que j'ai de différent? Je vais avoir une colonne supplémentaire changement. Donc ça, on l'avait un peu déjà vu la dernière fois. Euh et donc là ici les différentes factures euh différentes factures qui sont en inchangé enfin voilà qui était précédemment dans le reporting transmis et accepté. un changer ou rien. Je prouvais que rien c'est du coup ça n'apportait pas de bruit.


00:11:58

Fabien Riou: Et là c'est les modifications enfin c'est les changements qui ont été apportés sur ces factures là. Celle-ci a été modifiée, c'est-à-dire que le montant hors taxe de la facture a été corrigé côté AP et qu'on a réceptionné ce flux. Et donc je peux aller à la précétabilité directement pour remodifier si je le souhaite. C'est lui.
Paul Sorrentino: Alors le juste petite remarque,
Fabien Riou: Ouais.
Paul Sorrentino: le détail de ce qui a changé dans La facture à mon avis, il coûte
Fabien Riou: Ouais.
Paul Sorrentino: celui-là.
Fabien Riou: Alors peut-être qu'on aura juste modification modification de la
Audric Podmilsak: Après, je pense que c'est plus simple.
Fabien Riou: facture.com.
Paul Sorrentino: Ouais.
Audric Podmilsak: te faire un détail genre au cas par cas, genre si tu modifies le montant là dans dans le dans le tableau si tu as 2000 qui a changé et mettre euh mettre 2000 barrés, mettre 100 à côté,
Fabien Riou: Ouais.
Audric Podmilsak: c'est moins coûteux parce que c'est un div qu'on peut faire côté front euh dif à 10. Si c'est de l'autre côté comme tu l'as marqué avec à chaque fois les tags,


00:12:47

Fabien Riou: OK.
Audric Podmilsak: euh j'ai l'impression qu'il faut qu'on remonte là. Enfin en fait non, c'est pas le côté c'est coûte aussi,
Fabien Riou: OK.
Audric Podmilsak: je sais pas.
Fabien Riou: Bon euh bon ou sinon un tag modifié et puis après euh et
Paul Sorrentino: Je pense que le détail de ce qui a changé,
Fabien Riou: après Ouais ou c'est ça ou c'est ça
Paul Sorrentino: ça peut être vu dans une seconde US à mon avis puisque c'est quand même un autre
Fabien Riou: ?
Ludovic Lelievre: Ouais
Fabien Riou: Ouais oui. Nous ne nous emballons pas là trop là-dessus.
Ludovic Lelievre: ouais.
Fabien Riou: En effet, c'est juste un message mais en effet les wordings sont pas encore très bons là-dessus mais oui oui clairement euh
Paul Sorrentino: C'est
Fabien Riou: le le changement ajouté donc là euh euh donc la facture manquantes ajoutées. Bon, les boardings sont pas encore très bons mais en gros ça a été ajouté par rapport à ce qui a été voilà ce qui a été supprimé. Et là si ça a été ajouté et là je peux vu que ça vient de la public.


00:13:38

Fabien Riou: Bon voilà, je vais pouvoir oui oui
Ludovic Lelievre: Non là là là là ça vient tu es dans un achat là je pense.
Fabien Riou: oui oui c'est vrai c'est vrai un achat.
Ludovic Lelievre: Faut voir les sources là parce que si tu es en là tu es en achat tout tout
Fabien Riou: Bon bref, OK, je reste en ajouter.
Ludovic Lelievre: tout redirige vers la préac
Fabien Riou: On supprime quand même. Ouais. Bon, OK, en effet, tout redirige. C'était pas le bon exemple. Je le ferai 60. Euh et là, supprimer pareil supprimer, ça a été supprimé. Donc cette facture a été présente dans le dans le transmis et donc c'est en état supprimé. Donc elle est bien là. Donc c'est à moi après de cliquer sur transmettre. Bon, avec le truc là, transmettre le rectificatif manuellement pour avoir cette dernière version de ce rectificatif avec ces factures là. Et ça ici rien n'a été rien n'a été changé sur cette sur ces
Audric Podmilsak: Donc du coup quand tu as un supprimer là en fait techniquement la plupart du temps il y aura il y aura deux actions rectificatives parce que


00:14:26

Fabien Riou: factures.
Audric Podmilsak: j'ai du mal ou alors enfin ou alors ils sont trompés, ils ont ils ont annoncé un truc en erreur mais souvent en fait c'est qu'ils se sont trompés par de date ou de trucs et ça va le créer dans une autre période.
Fabien Riou: Alors euh ça c'est on l'a un peu détaillé dans un document euh dans un document où si pour toute modification si c'est sur le TVA et tout c'est en état modifié Okay. Euh et du coup ça impacte le erecting en question celui-ci. Si par contre ça joue sur la période, c'est une modification côté préac sur la période et ben suivant la période et ben ça va impacter un ou deux rectificatifs, soit euh soit la euh soit la la modification de ce même eorting parce que la date correspond à la même période de ce même eorting, soit ça change de reporting et du coup ça enlève euh ça enlève ça clé met supprimé sur la reporting en question et ça va créer un autre rectificatif avec cette avec ce
Paul Sorrentino: créer ou non.
Fabien Riou: reporti.
Paul Sorrentino: D'ailleurs, si tu mets euh si tu mets la nouvelle date sur la date de d'un reporting qui a pas été transmis, il est juste ajouté quoi.


00:15:50

Fabien Riou: Oui oui. Voilà.
Ludovic Lelievre: Ouais.
Fabien Riou: Après ça crée ou ça garde sur le même reporting ou ça crée un nouveau un nouveau reporting
Audric Podmilsak: F
Paul Sorrentino: H
Fabien Riou: soit normal soit soit rectifiquant.
Paul Sorrentino: on va on va avoir des liens assez vénères des fois parce que ça veut dire que tu peux avoir euh un nombre infini de reporting qui sont liés. Bon, ça va être rare mais tu changes deux factures ou tu changes la date, tu peux potentiellement lier trois reporting entre eux,
Audric Podmilsak: Bah benah non parce qu'en fait en soi Ah si tu es quand même non tu es toujours lié à un seul
Paul Sorrentino: quoi.
Audric Podmilsak: reporting. que si tu en supprimes une qui était pas dans le bon,
Fabien Riou: Ouais.
Audric Podmilsak: tu vas venir rectifier un truc qui existe. Mais tu auras qu'un seul lien. Même si tu l'ajoutes dans un autre, celle-là, elle va il y aura qu'un seul lien à chaque fois.
Paul Sorrentino: Ouais, mais après tu prends une deuxième facture et tu fais pareil mais avec une autre
Audric Podmilsak: Ah, dans l'autre sens.


00:16:38

Audric Podmilsak: Ouais. Oui.
Paul Sorrentino: date.
Audric Podmilsak: Un un reporting initial peut être enfin même n'importe quel reporting du coup peut être lié à N rectification à droite. Oui,
Paul Sorrentino: Ouais.
Audric Podmilsak: ça c'est vrai ça. Après, est-ce que c'est gênant?
Paul Sorrentino: Non, je pense pas. Mais
Audric Podmilsak: En tout cas, je pense qu'il faut qu'on arrive vraiment bien à segmenter le le je crée un rectificatif que tu nous montres là.
Paul Sorrentino: euh
Audric Podmilsak: Donc du coup, un rectificatif et son et sa façon de vivre de tous les cas qui peuvent créer des rectificatifs à droite à gauche, enfin tous les scénarios qui sont en entrée
Ludovic Lelievre: Oui, je pense qu'il faut mettre faut mettre à part le la modification
Fabien Riou: Ouais.
Audric Podmilsak: quoi.
Ludovic Lelievre: euh d'une date de la modification d'un champ de
Fabien Riou: Ouais.
Ludovic Lelievre: la facture qui viendra toujours modifier la même période.
Audric Podmilsak: Tu veux dire on on pourrait commencer par faire un happy pass où on fait que de la modification d'un champ ou une


00:17:29

Ludovic Lelievre: Ouais.
Audric Podmilsak: facture depuis AP. Et alors là,
Ludovic Lelievre: Oui.
Audric Podmilsak: on a vraiment la la boucle la plus simple qu'on peut faire,
Ludovic Lelievre: Oui.
Audric Podmilsak: quoi.
Ludovic Lelievre: Ouais. Parce que la modification de la date, bah ça va être un merdier
Paul Sorrentino: Ouais,
Ludovic Lelievre: et
Paul Sorrentino: je pense qu'elle entraîne un paquet de H case qu'on n'est pas encore capable de voir celle-là.
Ludovic Lelievre: je Ouais. Je sais pas comment on peut se prémunir de ça dans un premier temps parce que c'est sûr qu'on je pense qu'on aura pas on aura on va développer d'abord la l'ajout modifié et suppression dans un même reporting rectificatif qui est déjà un gros morceau avant de s'attaquer à une rectification cross cross période. Donc ça c'est ça voir Ouais.
Audric Podmilsak: On peut le bouchonner, hein. C'està dire que au départ, on peut le bouchonner en disant"Bah OK, c'est impossible à faire euh et on on met le flux en erreur." Comme on le met on


00:18:16

Ludovic Lelievre: Oui oui oui, c'est ça. Oui, c'est ça. C'est ça, c'est ça. Du coup,
Audric Podmilsak: l'
Ludovic Lelievre: faudra avoir une règle de si tu modifies la date et que cette modification de date fait changer de période, on bloque ou même on bloque la la modification de date.
Paul Sorrentino: Hm.
Audric Podmilsak: après. Ouais.
Paul Sorrentino: Sache, sachant que sortie de mon chapeau, j'ai il y a la question se pose, c'est qu'est-ce que va vérifier derrière euh la DGFIP? Genre imagine tu fais une modification de facture d'un re enfin d'un d'un e-reporting vers un autre. Le le bouton transmettre il est manuel. Donc ça veut dire que tu pourrais potentiellement transmettre un rectificatif sans avoir transmis le deuxième. À ce compte là, tu aurais deux factures en doublon qui sont transmis à la DG FIP. Enfin c'est c'est je pense ça pose des questions derrière.
Audric Podmilsak: C'est quoi ton candidat? J'ai pas compris.
Paul Sorrentino: Imagine, je déplace une facture, j'ai transmis un reporting du 1er au 15 août et un autre du 15 au


00:19:08

Audric Podmilsak: Attends.
Paul Sorrentino: 30. Je prends ma facture du 1er au 15, je la déplace du 15 au 30, je transmets mon nouveau rectificatif du 15 au 30. Ta facture, elle est en doublon, elle est dans le premier 15 et dans le 1530 vu que tu as pas encore transmis l'autre rectificatif. Donc ça veut dire je pense qu'il faut les transmettre en simultané les deux sinon je sais pas.
Fabien Riou: Ouais, une facture ne peut pas être dans
Audric Podmilsak: Bah si tu en transmets qu'un des deux, l'initial il a il a l'initial est sur une période, il a une facture, tu la modifies,
Fabien Riou: de
Audric Podmilsak: elle va dans une autre période corrective. Donc tu la supprimes ici, tu l'ajoutes ici dans un autre une autre période de lignes en parallèle. Tuenvoies celle-là en rectificatif mais celle-là tu l'envoies pas. Le rectificatif ici qui est généré qui est autogénéré parce que nous ce qu'on veut c'est que ça génère de rectificatif où elle va être


00:19:58

Paul Sorrentino: Hm.
Audric Podmilsak: ajoutée et un va supprimée. Si tuen vois que un des deux, qu'est-ce qui se passe? Qu'est-ce qui se passe au niveau de
Paul Sorrentino: Est-ce que c'est Est-ce que tu peux déjà le faire
Ludovic Lelievre: Ouais.
Audric Podmilsak: la pas
Ludovic Lelievre: Oui. Bah du coup c'est c'est des supers questions et et ça montre que ça rend ce ce
Paul Sorrentino: ?
Audric Podmilsak: faire
Ludovic Lelievre: cas complexe et on va pas commencer par ça. Du coup, je vous propose qu'on le laisse enfin qu'on le garde dans nos têtes et qu'on
Audric Podmilsak: ? Tu as peut-être une option,
Ludovic Lelievre: le
Audric Podmilsak: c'est peut-être qu'il y a un ordre à respecter et qu'il faut d'abord faire la suppression pour pouvoir faire de la la
Ludovic Lelievre: Ouais.
Audric Podmilsak: jouable.
Ludovic Lelievre: Ouais. Mais du coup, ça serait euh potentiellement du coup une suppression automatique parce que comme ça on s'assure que la suppression le rectific de la suppression est déjà parti avant d'ajouter la facture dans euh bref


00:20:42

Paul Sorrentino: Ouais, enfin toujours est-il que je pense que ça tu as raison.
Ludovic Lelievre: ça Ouais pour l'instant du
Paul Sorrentino: Ça fait l'objet d'un autre autre quest.
Ludovic Lelievre: coup ça faut faut qu'on se mette qu'on se note de mettre une règle pour bloquer ces cas-là côté AP au moment où on on commence toute Yeah. le chantier de la
Fabien Riou: Ouais,
Ludovic Lelievre: rectification.
Fabien Riou: je aussi euh je vais partager un cas aussi où même si euh bon là je l'ai fait vraiment sur une facture facture de vente. Bon, ça sera plus une transaction B2C. À voir si on offre la suppression manuelle d'une facture B2B via public AP ou pas. Et sinon, ça va être une transaction. Euh déjà transmis, bah je pars d'un transmis de cette vente là. Je vais vouloir supprimer cette facture là ou ce paiement ou cette transaction et ben je vais pouvoir supprimer supprimer ça et là ça va me dire sur supprimé dans un rectificatif à rectifier bon pour la période et donc là ça va créer le rectificatif ici dans un à transmettre à rectifier et c'est là où je vais avoir du coup ma facture qui va être supprimée et que je vais devoir retransmettre à l'administration fiscale.


00:21:52

Paul Sorrentino: Ok.
Audric Podmilsak: Alors, attends sur sur les soit donc ça on l'autorise sur les factures de vente que pour le
Fabien Riou: Alors
Audric Podmilsak: BC on pas dit que ça allait être fait que par public API celle d'ap c'est que dans AP par
Fabien Riou: voilà,
Audric Podmilsak: contre on autorise de le
Fabien Riou: ça c'est une question c'est une question qu'on qu'on se posait. Est-ce que on offre la possibilité via public API pour les factures B2B internationales et euh tout ce qui est B2C, la possibilité de supprimer euh manuellement alors que ça a été envoyé euh via la public API parce qu'aujourd'hui euh ça permet que d'envoyer quoi la public API.
Ludovic Lelievre: C'est déjà le cas dans le l'initial. Dans les signal,
Fabien Riou: Voilà.
Ludovic Lelievre: on permet déjà de supprimer une facture manuellement qui a été créée par la public parce qu'on a d'ailleurs pas d'end point pour supprimer.
Fabien Riou: Voilà. Donc dans tous les cas, cette fonctionnalité là sera vraiment à partir tuimportes une transaction B2C, un paiement B2C, tu l'importes manuellement et tu as été transmis, tu l'as transmis, tu dois pouvoir aussi supprimer cette cette ce paiement B2C.


00:23:08

Ludovic Lelievre: Et là, on est d'accord qu'ici Fabien au moment où on crée le rectificatif, tu as du coup cette ligne suppression et toutes les lignes,
Fabien Riou: Ouais.
Ludovic Lelievre: toutes les autres lignes de l'ancien qui apparaissent.
Fabien Riou: Oui, en effet qui apparaît
Ludovic Lelievre: Bon, qui j'imagine sont coûteux à faire en proto mais ça serait ça le comportement.
Fabien Riou: mais c'est tout à fait ça. Tu auras le l'ensemble des autres lignes. Les autres lignes c'est vrai qu'on le voit pas. Et donc du coup aussi ça met l'historique en cours de rectification parce que là on est dans le projet de de rectification à rectifier et on a ici l'historique, ça a bien été transmis transmis, validé euh
Ludovic Lelievre: Et plutôt plutôt que de changer le statut,
Fabien Riou: et transmis.
Ludovic Lelievre: est-ce qu'on a pas intérêt à garder le statut?
Fabien Riou: Ouais peut-être.
Ludovic Lelievre: B transmis ou accepter parce que lui au final il va continuer d'évoluer.
Fabien Riou: Ouais.
Ludovic Lelievre: et d'ajouter un autre tag qui dit que bah lui euh il est en plus il est en cours de il est en cours de rectification mais mais sans toucher au statut parce qu'en fait si ça se trouve bah il est dans un état je sais pas où c'est chez CI mais on l'a pas


00:24:10

Fabien Riou: Il a bien été transmis celui-là.
Ludovic Lelievre: encore il peut potentiellement passer de transmis accepté en cours de rectification
Fabien Riou: Ouais. Ouais. Je le mettrai à l'intérieur euh ce en cours. Euh euh celui-ci en cours parce que là d'avoir un deuxième tag là-dedans, c'est
Ludovic Lelievre: parce que techniquement ça oui,
Fabien Riou: Attends.
Ludovic Lelievre: il sera accepté et il il est toujours à ce stade accepté par l'administration fiscale.
Fabien Riou: Ouais. Oui.
Audric Podmilsak: Oui,
Fabien Riou: Oui.
Audric Podmilsak: c'est en fait c'est statificatif plutôt une colonne part en fait.
Paul Sorrentino: Ouais.
Fabien Riou: Oui. Oui.
Audric Podmilsak: M.
Fabien Riou: Et du coup, celui-ci sera en lecture lecture seule. Tu ne pourras pas euh resupprimer. Là, il y aura plus ça. Tu pourras que voir ce qui a été historisé, mais tu ne pourras pas supprimer et tu pourras pas recréer un rectificatif sur ça parce que tu as déjà un projet de rectification sur la même période, sur la même chose qui est déjà qui est déjà en cours.


00:25:04

Fabien Riou: Donc limite un petit bandeau là-dessus, un projet en cours.
Paul Sorrentino: Ouais.
Fabien Riou: Tiens, tu cliques dessus et tu es renvoyé vers le vers
Paul Sorrentino: Bon après je vois enfin pourquoi ne pas lui permettre de le supprimer d'ici aussi c'est
Fabien Riou: la
Paul Sorrentino: juste qu'au lieu de créer un rectificatif tu modifies le
Fabien Riou: Ouais, C'est quoi
Ludovic Lelievre: Ça revient un peu au même.
Paul Sorrentino: Oui.
Ludovic Lelievre: C'estàd que dans dans le texte,
Paul Sorrentino: Ça revient au
Fabien Riou: ?
Paul Sorrentino: même.
Ludovic Lelievre: il faudrait quand même lui préciser que là ça va pas créer mais ça va ajouter son action dans le rectificatif.
Paul Sorrentino: Ah oui, la dialogue ouais de confirme.
Ludovic Lelievre: Donc autant autant le renvoyer vers le rectificatif une fois qu'il est ouvert.
Paul Sorrentino: Ouais.
Fabien Riou: Oui, c'est ça. Complexifier un peu la
Audric Podmilsak: et Et juste sur le tableau d'avance, tu viens plutôt que d'avoir ce statut en cours de correction,
Fabien Riou: chaussure.
Audric Podmilsak: est-ce que ici le mieux c'est pas d'avoir statut et à côté rectificatif?


00:25:51

Audric Podmilsak: Tu as une une ligne avec l'ID et quand tu cliques dessus, tu vas sur le rectificatif parce
Fabien Riou: Est-ce que tu as besoin d'avoir le listing là-dessus?
Audric Podmilsak: que
Fabien Riou: Parce que la majorité seront pas en rectificatif. Enfin, est-ce qu'il y a besoin d'avoir ça ici? Je suis pas
Audric Podmilsak: bah c'est juste que là en fait comme disait Ludo avant,
Fabien Riou: sûr.
Audric Podmilsak: c'est que ça c'est trompeur en cours de rectification.
Fabien Riou: Oui. Oui. Alors, je suis d'accord. On mettra transmis. Mais est-ce que du coup tu as besoin d'avoir ce listing là-dessus? Parce que là, c'est vraiment l'historique. Qu'est-ce que tu as été transmettre? Et là-dedans euh euh voilà,
Audric Podmilsak: Non, ça peut ça peut être comme tu l'as dit avant dans la vue d'après et avoir le lien effectivement c une idée bon je sais pas pas forcément une bonne idée.
Fabien Riou: c'est ça.


00:26:31

Ludovic Lelievre: et et mais le lien où il serait fait il serait accessible j'imagine dans des deux sens.
Fabien Riou: C'est
Ludovic Lelievre: On pourrait avoir le lien d'ici vers le rectificatif et idem du rectificatif
Fabien Riou: Ouais. Oui.
Ludovic Lelievre: vers son précédent.
Audric Podmilsak: Bah ouais oui
Ludovic Lelievre: On a les deux.
Audric Podmilsak: ouis
Paul Sorrentino: Après moi le double tag,
Ludovic Lelievre: Non.
Paul Sorrentino: je trouve pas ça déconnant
Ludovic Lelievre: Ouais.
Audric Podmilsak: je pense qu'il faut il faut distinguer les deux parce que ça va nous ça va indure en erreur c'est déjà compliqué Oui.
Paul Sorrentino: mais sans sans rajouter une colonne effectivement. No. Juste mettre le les deux tags dans la même colonne transmis en cours de
Fabien Riou: Je suis pas moi je suis pas convaincu que le tag sert à quelque chose dans la partie historique franchement au
Paul Sorrentino: rectification.
Fabien Riou: final parce que là c'est vraiment pourquoi il a besoin d'avoir n historique c'est pour euh c'est pour voir ce qui est ce qui a été
Audric Podmilsak: C'est quand même pas mal si ici tu as un truc avec euh un tag quelque part dans cette ligne là.


00:27:16

Fabien Riou: rhistorisé.
Audric Podmilsak: Peut-être pas dans la T colon statut, peut-être sur la période période, j'en sais rien. Un tag qui dit euh correctif. C'est comme ça, tu sais que celle-là, elle a été corrigée et si tu cliques sur le tag, ça t'envoie vers le bon.
Fabien Riou: Ouais.
Audric Podmilsak: Ça c'est pas si c'est pas si coûteux ça.
Fabien Riou: Non non, c'est pas
Paul Sorrentino: M.
Audric Podmilsak: Juste tu arrives sur tu arrives sur tes trucs sur ton historique et tu vois pour enfin tu sais plus comment le retrouver, tu peux le retrouver d'ici quoi.
Fabien Riou: Ouais. Peut-être que tu vas avoir dans un transmettre, tu vas avoir tellement après tu les as ici quoi dans transmettre.
Audric Podmilsak: Ah.
Fabien Riou: Mais
Ludovic Lelievre: Mais tu pourrais filtrer en fait au final si tu veux si tu veux filtrer,
Fabien Riou: OK.
Ludovic Lelievre: on pourrait ajouter un filtre de affiche-moi tous ceux qui sont en cours de
Paul Sorrentino: Moi je pense que le backlink depuis l'historique,
Ludovic Lelievre: rectification.


00:28:02

Paul Sorrentino: il est vra il est franchement pas MVP à mon avis.
Audric Podmilsak: Oi,
Fabien Riou: Bon, après ça c'est des petits c'est des petits détails je pense au final ça.
Ludovic Lelievre: Ouais, ça c'est
Fabien Riou: Mais OK. Euh en cours d'actification avec un historique ici, un historique ici,
Ludovic Lelievre: un historique. C'est quoi l'historique?
Fabien Riou: bah c'est tac. celui-ci euh celui ce qu'on avait prévu. Parce que
Ludovic Lelievre: parce que du coup est-ce qu'on a besoin d'un là le a rectifié lui il est du coup il est lié à un précédent
Fabien Riou: il est lié un précédent là que tu vois on pourra mettre lien vers le l'historique tois ici
Ludovic Lelievre: mais mais on aurait que deux
Fabien Riou: euh on aurait
Ludovic Lelievre: événements Mais
Paul Sorrentino: Bah pas forcément.
Fabien Riou: que tu as les dates des différentes
Paul Sorrentino: Si tu as rectifié 15 fois ton truc, euh
Ludovic Lelievre: mais ah tu le fais,
Fabien Riou: rectifications quoi.
Ludovic Lelievre: tu as toujours les liens de lien de lien?


00:28:52

Paul Sorrentino: ça
Fabien Riou: Oui,
Ludovic Lelievre: OK OK le début. OK ou
Fabien Riou: c'est encore une fois c'est qu'un objet un objet du reporting quoi sur une date
Ludovic Lelievre: OK.
Fabien Riou: sur un
Ludovic Lelievre: Historique des rectifications. Ouais des
Paul Sorrentino: que cette historique, du coup,
Ludovic Lelievre: OK.
Paul Sorrentino: il faudrait qu'il soit identique pour toutes les périodes qui concernent le même truc, quoi. Si tu as fait 15 fois un rectificatif sur la même période, il faudrait que l'historique des événements soit identique pour les 15.
Audric Podmilsak: C'est coûteux hein. C'est qu'il faut à chaque fois les enfin c'est coûteux pour aller
Paul Sorrentino: Ouais,
Audric Podmilsak: parcour.
Paul Sorrentino: faut voir que faut faut penser le truc pour décorer les enfin Ouais.
Fabien Riou: Pourquoi? Comment ça c'est en quoi parce que du coup à chaque transmission et ben tu crées un événement sur le l'objet reporting.
Audric Podmilsak: Ouais, mais juste que en gros quand tu veux afficher historique, tu es obligé d'aller prendre l'ID de celui-là et dire"OK, quels sont mes parents? Quels sont tous les parents de mes parents?


00:29:51

Ludovic Lelievre: H
Audric Podmilsak: Mes parents et dans l'autre sens quels sont tous les enfants de mes enfants de mes enfants Donc en gros, parce que tu peux en
Paul Sorrentino: Ah oui, mais ça c'est une proposition M. de de d'un plem technique que tu fais. Mais une autre proposition, c'est d'avoir un historique qui a un objet qui a un objet indépendant et qui va se qui va s'attacher à ni reporting. Au quel cas tu as un seul historique qui concerne plusieurs
Audric Podmilsak: Ouai ben mais dans ce cas dans toi ce que tu proposes c'est de de le construire de construire cette projection à chaque fois qu'on fait des
Paul Sorrentino: reporting.
Fabien Riou: Ah
Audric Podmilsak: actions de projection et à la fin que tu puisses la retrouver par un ID.
Fabien Riou: ouais.
Audric Podmilsak: Oui,
Paul Sorrentino: Ouais.
Audric Podmilsak: bon façon de le voir mais dans tous les cas dans les deux cas
Fabien Riou: Bon,
Audric Podmilsak: c'est une future coûteuse dans les deux cas.
Fabien Riou: c'est peut-être c'est en effet c'est peut-être c'est peut-être pas du tout
Ludovic Lelievre: Ouais,
Audric Podmilsak: C'est ça que je veux


00:30:33

Ludovic Lelievre: je pense que le le MVP c'est d'avoir le lien avec le précédent,
Fabien Riou: c'est
Audric Podmilsak: dire.
Paul Sorrentino: Ouais.
Ludovic Lelievre: d'avoir les liens entre le rectificatif et son et son précédent et le précédent vers son
Fabien Riou: Ouais.
Ludovic Lelievre: rectificatif.
Fabien Riou: C'est ça.
Paul Sorrentino: Ouais.
Audric Podmilsak: Bah surtout qu'on fait des on fait un peu des plans sur la comète de il va y avoir n rectificatif chaîné.
Ludovic Lelievre: Oui, non,
Audric Podmilsak: On sait pas en fait.
Ludovic Lelievre: c'est
Fabien Riou: Mais
Paul Sorrentino: D'ailleurs, juste pour un sujet corrélé sur ton parcours utilisateur Fabien là quand tu as créé un
Ludovic Lelievre: sûr.
Paul Sorrentino: rectificatif, tu avais la dialogue attention, tu vas créer un rectificatif quand tu le valides, tu reviens sur la liste des des rectificatifs. Moi, j'irai directement sur la vue du rectificatif, non? parce que sinon justement il va être paumé le type.
Fabien Riou: oui oui oui je Bah là tu
Ludovic Lelievre: Nej.
Fabien Riou: es dedans


00:31:14

Paul Sorrentino: Ouais mais là tu es dans la liste.
Ludovic Lelievre: Mais dedans dans celui qui est créé du avec la
Paul Sorrentino: Moi j'irai directement dans le rectificatif.
Fabien Riou: euh ouais je suis d'accord je suis
Ludovic Lelievre: ligne supprimée et l'ensemble des lignes.
Fabien Riou: d'accord je suis d'accord je suis d'accord parce que c'est vrai que tu le vois pas là il me l'a mis là là mais en
Paul Sorrentino: Hm.
Ludovic Lelievre: OK.
Fabien Riou: effet je ne le vois pas Ouais, très cool.
Ludovic Lelievre: Et du coup la le dernier la dernière étape c'est une fois que tu transmets,
Fabien Riou: OK.
Ludovic Lelievre: si tu as un lien avec un reporting dans historique, c reporting dans historique passe en annulé.
Fabien Riou: Hm. Si
Ludovic Lelievre: celui qui est tagué en cours de rectification,
Fabien Riou: tu
Paul Sorrentino: Voilà.
Ludovic Lelievre: tu as le transmis h/ accepté, on sa pas tirer euh
Fabien Riou: Ah oui oui
Paul Sorrentino: annuler ou rectifier plutôt peut-être non
Ludovic Lelievre: lui.
Paul Sorrentino: ?
Fabien Riou: ouis parce que du coup la historique on parlerait vraiment de flux
Audric Podmilsak: Parce que annuler,


00:32:11

Fabien Riou: là
Audric Podmilsak: c'est annulé avant d'avoir été transmis.
Paul Sorrentino: Hm.
Ludovic Lelievre: Oui oui non oui non ça peut être rectiféré.
Fabien Riou: parce que là du coup ça veut dire que c'est tu parles pas d'objets tu aurais une ligne. Tur Ah oui mais là tu
Audric Podmilsak: Le statut le statut passe à rectifier.
Fabien Riou: aurais
Audric Podmilsak: Une fois que le que le rectificatif associé et bien effectivement alors c'est la question c'est est-ce qu'il est une fois qu'il est transmis, une fois qu'il est accepté dès
Ludovic Lelievre: Non, une fois qu'il est transmis
Fabien Riou: une fois qu'il est transmis,
Audric Podmilsak: qu'il Oui,
Fabien Riou: il y a une deuxième ligne qui apparaît du coup parce
Audric Podmilsak: tu en auras une pour le correctif. En gros, si tu en avais qu'un dans ton truc que tu corriges une fois, donc ça va créer un nouveau. Donc c'est là que la question se pose. Tu avais un encorctification qui était un peu trompeur.
Paul Sorrentino: Oui.
Audric Podmilsak: Et ce qui pourrait ce qu'on pourrait dire,


00:32:56

Fabien Riou: Ouais. Non non, final c'est
Audric Podmilsak: c'est qu'au final plutôt d'avoir En cours de rectification, on n pas ce statut intermédiaire et quand le nouveau est transmis, l'autre passe en rectifier.
Paul Sorrentino: Alors transmis enfin d'un point de vue expérience client ça se comprend mais je pense que si
Audric Podmilsak: Alors
Fabien Riou: accepté
Paul Sorrentino: tu le bascules directement à transmis imagine que le rectificatif est rejeté derrière tu as plus enfin c'est faux du
Audric Podmilsak: c'est pour Ouais et c'est pour ça que je pense que c'est plus simple de mettre ce que je disais avant, le tag rectificatif. Tu as un rectif rectificatif qui est associé.
Paul Sorrentino: Coup
Audric Podmilsak: Alors après en avoir plusieurs donc c'est ça qui est compliqué mais normalement tu peux en avoir qu'un seul à Ah non tu peux en avoir plusieurs faire tu peux avoir 15000 rectificatifs.
Fabien Riou: Ouais mais alors du coup on n'est plus là en mode objet d'un reporting où il y en aura qu'un seul et plus là on est sur un listing historique des différents flux de reporting euh transmis quoi. Un tel jour qui a été accepté et un autre qui était plus en rectif rectificatif et qui a été transmis et accepté quoi.


00:33:58

Fabien Riou: C'est ça qui
Audric Podmilsak: Ah.
Fabien Riou: me
Paul Sorrentino: Parce que toi dans ta vision, tu voulais que pour une période, il y ait toujours qu'une seule ligne.
Fabien Riou: Ouais. En fait, moi alors j'avais proposé ça au début mais en effet c'était peut-être céit ça demandait un basculement de se dire si tu rectifies celui-là disparaît de transmis enfin de de d'ici d'historique et rebascule dans un transmettre quoi. Et avec Ludo, c'est vrai qu'on se disit ça peut peut-être un peu ça peut peut-être un peu choqué. Alors que dans historique, il est là pour voir tiens,
Paul Sorrentino: M.
Fabien Riou: j'ai l'historique de tout ce qui a été transmis et puis au moins voilà et qu' a et qui a un projet de rectificatif et donc du Luc où c'est un duplicat de ce qui historisé envoyé et du coup on crée un projet de rectificatif qui va être dans un transmet
Audric Podmilsak: Non mais par contre par contre dans ce que vous dites ce qui peut être sympa, c'est que la première étape, je sais pas si elle est vraiment avoir les deux au départ tant qu'il est pas transmis,


00:34:44

Fabien Riou: Eh
Audric Podmilsak: c'est peut-être plus simple. Par contre, dès que tu as un correctif qui est fait, c'est forcément sur une période. Et là-dessus, tu peux dire que dès que tu en as deux sur la même période qui rentrent dans historique, l'ancien il dégage et le nouveau il arrive avec un tag correctif ou pas,
Paul Sorrentino: Ouais, je suis pas trop d'avis de cacher des infos à l'utilisateur. Je trouve que l'historique plus il est exhaustif et mieux c'est à mon
Fabien Riou: ouais.
Audric Podmilsak: Mais
Fabien Riou: Donc en fait
Ludovic Lelievre: Après après on peut les on peut les filtrer par défaut les rectifier pour qu'il
Paul Sorrentino: avis.
Fabien Riou: soit
Ludovic Lelievre: pour que disparaisse de cette liste mais
Fabien Riou: Ouais mais soit on est plus en mode soit on est plus en mode
Audric Podmilsak: c'est
Fabien Riou: date de date de d'envoi où là on est plus en mode flux voilà voilà ce qui a été envoyé transmis et accepté et là on a tout l'historique et il peut y avoir de tr de tr lignes
Audric Podmilsak: C'est c'est trié comment ce tableau?


00:35:38

Audric Podmilsak: Parce qu'en fait si c'est si c'est trié par entité plus puis plus période ça marche. Non, ça marche pas parce que du coup tu es coincé.
Ludovic Lelievre: Non, tu aurais dû rectifier au milieu.
Audric Podmilsak: Ouais.
Fabien Riou: Hm.
Paul Sorrentino: Moi je le triai par date d'envoi honnêtement.
Audric Podmilsak: Et bah non parce que du coup tu vois pas tes rectificatifs, ils sont cachés.
Paul Sorrentino: Ben si justement tu les verras au moment où tu les envoies parce que si tu rectifies une facture enfin si tu rectifies
Audric Podmilsak: Tu vois?
Paul Sorrentino: une période qui date d' 1 an, ça veut dire que ton rectificatif il va se passer en page 25 et tu le verras plus jamais
Audric Podmilsak: quoi.
Paul Sorrentino: Ouais. Mais du coup à l'inverse, tu vois pas tu vois pas euh les périodes associées.
Audric Podmilsak: Donc du coup, tu les perds complètement, tu mets en avant ce qui vient d'être envoyé.
Paul Sorrentino: Ouais ouais c'est c'est comme question.
Audric Podmilsak: Alors ouais, non simple. Mais si tu tries par période, même si alors c'est un peu compliqué parce que tu envoies un rectificatif là maintenant alors que c'est un truc il y a un an, tu le vois pas mais au moins tu sais toujours comment tout trouver par période.


00:36:36

Audric Podmilsak: Et j'ai l'impression que enfin faut se poser la question de comment est-ce que les comptables bossent, tu vois. Mais eux ce qui les intéresse, c'est pas la date d'envoi, c'est plutôt euh OK. Sur le mois, sur cette période-là, qu'est-ce que vous déparé
Ludovic Lelievre: ça là.
Fabien Riou: c'est plus en mode pour moi c'est plus un objet de se dire voilà sur cette période là qu'est-ce que j'ai quoi.
Ludovic Lelievre: Ouais.
Audric Podmilsak: ?
Fabien Riou: Qu'est-ce qui a été envoyé,
Ludovic Lelievre: Oui.
Fabien Riou: qu'est-ce qui a été transadministration fiscale.
Ludovic Lelievre: Qu'est-ce que quelle information à l'administration fiscale
Fabien Riou: Voilà,
Paul Sorrentino: Ouais.
Fabien Riou: c'est pour ça c'est pour ça que le mode objet d'un reporting,
Ludovic Lelievre: ?
Fabien Riou: il est unique et làdedans, tu as tout dedans, quoi.
Paul Sorrentino: H
Fabien Riou: Tu as tout dedans et il est unique. Et ouais.
Ludovic Lelievre: Et comment tu reviens si tu as besoin de d'audit que tu as envoyé à l'administration fiscale


00:37:12

Paul Sorrentino: bah c'est ça.
Ludovic Lelievre: ?
Paul Sorrentino: Juste vérifier que le statut il est bien passé à transmis ou accepter. Si tu fais un rectificatif d' un an, tu es obligé d'aller en page 15 pour trouver ton truc.
Ludovic Lelievre: Je pense que tout ce qui est envoyé, accepté à un moment donné par l'administration fiscale, on doit le le mettre à disposition d'une certaine manière au client,
Paul Sorrentino: Ok.
Ludovic Lelievre: au comptable s'il a besoin.
Audric Podmilsak: Ah oui.
Fabien Riou: Ouais mais alors du coup Mais alors attends mais non mais au final euh une fois que là il a été il est rectifié Là, je clique sur transmettre le rectificatif. Là, il passe en là, il passe en dans l'historique et cet ob là en mode en cours de transmission transmis,
Ludovic Lelievre: trans
Fabien Riou: accepté. Bref, il y a pas de en cours de toute façon dans tous les cas, il y a pas de en cours et pas transmis avec une date d'événement euh une date d'événement là pour le coup euh à jour quoi, tu vois. et avec la dernière version qui a été
Ludovic Lelievre: Et du coup tu Oui, mais du coup le le comptable,


00:38:07

Fabien Riou: euh
Ludovic Lelievre: il perd ce qui a été envoyé précédemment à l'administration fiscale.
Audric Podmilsak: Ouais, mais est-ce que est-ce
Paul Sorrentino: M.
Fabien Riou: mais c'est toujours Non parce qu'il y aura l'événement l'événement de la date de la date de la date et ce qui a été
Audric Podmilsak: que
Fabien Riou: en sûr c'est toujours la dernière version qu'on c'est toujours
Audric Podmilsak: Ouais, je suis d'accord. Il est à jour. Moi moi je pense que ce qu'il faut ici c'est montr c'est montrer une ligne par période parce qu'en fait c'est
Fabien Riou: il est à jour sur la dernière version quoi.
Audric Podmilsak: c'est le le après la façon dont on les ordonne c'est comme on veut mais pour moi une ligne par période moi je les
Paul Sorrentino: M.
Fabien Riou: Ouais,
Audric Podmilsak: ordonnerai par période des croissantes parce qu'en fait une période ce sera il y aura toujours que une période il y
Fabien Riou: c'est ça. Voilà.
Audric Podmilsak: aura toujours que un une transmission même si tu as cinq rectificatifs il y aura quand même toujours que une seule


00:38:43

Fabien Riou: Oui, c'est unique
Audric Podmilsak: période avec la dernière la dernière qui prime et et en fait les liens entre les différents trucs qui bougent
Paul Sorrentino: Ok.
Fabien Riou: avec la
Audric Podmilsak: d'un à l'autre Ça à la rigueur c'est pas on en a besoin nous pour le construire mais On s'en fout.
Fabien Riou: Ouais.
Audric Podmilsak: C'estàd que ce qui compte, c'est d'afficher au client,
Fabien Riou: Oui,
Audric Podmilsak: OK,
Fabien Riou: la dernière.
Audric Podmilsak: sur la période de cette période là, tu as déclaré ces factures
Fabien Riou: Oui.
Audric Podmilsak: là.
Fabien Riou: et qu'il y a dans historique, il y a qu'un seul objet e reporting.
Paul Sorrentino: Eu
Fabien Riou: Il y a qu'un seul objet en de sur une une seule et même période.
Audric Podmilsak: C'est c'est c'était un petit OK. Pourquoi tu es pas convaincu de de
Paul Sorrentino: en vrai, j'ai pas d'avis parce que je suis pas comptable donc j'ai énormément de mal à savoir ce qu'attend le
Audric Podmilsak: de
Paul Sorrentino: client.


00:39:25

Paul Sorrentino: Moi, c'est juste d'un point de vue purement connaissance du l'outil. Je suis limitatif sur le fait de cacher enfin pas cacher les informations mais de pas montrer l'exhaustivité de ce que tu as transmis, tu
Audric Podmilsak: Ouais, mais c'est mais après rien ne t'empêche dans cette période là de dire"OK,
Paul Sorrentino: vois.
Audric Podmilsak: quand tu ouvres la période du 1er janvier au 31 mars, le premier trimestre, j'ai déclaré ça et ça en fait ça fait l'état de cinq rectificatifs parce que je me suis trompé,
Fabien Riou: Oui, c'est ça. Ouais.
Audric Podmilsak: tu vois. Ça rien n'empêche de l'afficher ici. Mais au final ce qui compte demain, tu tu prends ton cas pour les impôts. Je sais pas, moi je me suis trompé là, j'avais oublié un truc, j'ai renvoyé un rectificatif, je m'en fous du premier que j'ai envoyé.
Paul Sorrentino: Oui,
Fabien Riou: Mais oui,
Paul Sorrentino: c'est
Audric Podmilsak: ce qui m'attend c'est le 2è tu vois


00:40:05

Fabien Riou: c'est fout de de des différents événements de ce que tu as envoyé le premier temps.
Paul Sorrentino: vrai.
Fabien Riou: Le l'objectif c'est de voir la dernière version que tu envoies qui est la plus à jour.
Paul Sorrentino: Ouais. Ouais. Non mais je suis OK, je suis d'accord.
Fabien Riou: Et donc là, tu as été transmis, tu as transmis ça, tu as envoyé deux factures, même si ça a été modifié, ajouté la juste avant, tuas transmis ça et ben c'est ça qui est la plus à jour avec l'administration fiscale. Point quoi.
Paul Sorrentino: Ouais.
Audric Podmilsak: Ne.
Fabien Riou: Pas besoin,
Paul Sorrentino: OK.
Fabien Riou: tu as pas besoin de savoir le premier rectificatif qu'on avait fait, on a envoyé ça quoi. Enfin,
Paul Sorrentino: Non non mais c'est c'est Ouais,
Fabien Riou: il s'en fout.
Paul Sorrentino: c'est je suis d'accord.
Ludovic Lelievre: Et du coup, ça serait à quel moment du coup qu'on ferait cette bascule?
Paul Sorrentino: OK.
Ludovic Lelievre: parce que au moment où le rectificatif passe de transmettre à historique, il passe en statut transmis mais techniquement il est pas encore


00:40:48

Fabien Riou: Ouais,
Ludovic Lelievre: il il est pas encore accepté par l'administration fiscale.
Fabien Riou: bah là il faut le voir. OK,
Ludovic Lelievre: Donc c'est encore c'est encore c'est encore c'est l'ancien.
Fabien Riou: là il part d'ici.
Ludovic Lelievre: C'est si l'administration fiscale à cette tot là regarde les ses comptes. C'est le c'est l'ancien reporting qui fait qui source de vérité.
Fabien Riou: Oui.
Audric Podmilsak: Ouais, mais après ici tu peux peut-être l'afficher dans dedans en fait.
Fabien Riou: Vo
Audric Podmilsak: C'estd que pour qu'on comprenne ça reste la même période mais tu peux afficher que en fait en gros il y a deux informations.
Fabien Riou: là.
Ludovic Lelievre: Ouais.
Audric Podmilsak: C'est quel est quel est son statut et quel est si c'est un crtifatif ou pas tu vois. Mais du coup si tu si c'est rectificatif, je pense que le statut il devient le nouveau statut, tu vois.
Fabien Riou: Oui,
Audric Podmilsak: Du coup,
Fabien Riou: devient le en cours d'enregistrement ici.


00:41:32

Fabien Riou: Il reste dans la transmettre ici dans en cours d'enregistrement.
Ludovic Lelievre: Mir
Fabien Riou: À partir du moment où on n pas la validation de la DGFI comme quoi ça a pas été
Audric Podmilsak: pas
Fabien Riou: accepté, et ben il passe pas dans historique. à partir du moment où il s'est accepté, et ben il passe ici dans l'historique et à
Ludovic Lelievre: du coup ça a pas le même comportement que pour les initiales.
Paul Sorrentino: Ouais,
Fabien Riou: jour
Paul Sorrentino: c'est ça le truc,
Ludovic Lelievre: là
Paul Sorrentino: c'est que c'est deux conforement différent du coup.
Fabien Riou: Ah.
Audric Podmilsak: dans le table historique. Ça
Ludovic Lelievre: bah dans pour les reporting initiaux à partir du moment où on transmet àedim, on bascule de à transmettre à historique et on met le
Fabien Riou: Là, il faudra changer pour moi. Il faud changer. Et toi là,
Ludovic Lelievre: statut
Fabien Riou: c'est limite c'est accepté. C'est pas transmis, c'est accepté. C'est accepté par la DG fip quoi
Ludovic Lelievre: et pourquoi du coup si à partir du moment où c'est transmis,


00:42:13

Fabien Riou: tout.
Ludovic Lelievre: pourquoi on est du coup on dégage pas l'autre et c'est lui qui pr il est transmis et il sera
Paul Sorrentino: Parce que dans le cas d'un correctif,
Ludovic Lelievre: Euh
Paul Sorrentino: c'est pas forcément vrai.
Fabien Riou: On dégage pas l'autre.
Ludovic Lelievre: ouais.
Audric Podmilsak: Ouais mais si mais pour moi je pense la Ouais.
Fabien Riou: C'estàd
Ludovic Lelievre: Pourquoi il prend pas pourquoi et pourquoi il prend pas la place de l'autre? Du coup, au moment où on on transmet le rectificatif,
Fabien Riou: Ouais.
Ludovic Lelievre: il bascule dans historique et il prend et il prend la place de et il se met en
Fabien Riou: Oui, il prend la base.
Paul Sorrentino: et il se met en transmis.
Fabien Riou: Oui, transmis avec la mise à jour
Ludovic Lelievre: transmis.
Paul Sorrentino: Ouais, mais ça ça fonctionne jusque-
Fabien Riou: ici.
Audric Podmilsak: Ouais.
Paul Sorrentino: là. Par contre, si ton correctif est
Ludovic Lelievre: Mais là,
Paul Sorrentino: rejeté,
Ludovic Lelievre: on retombe sur le même problématique que si ton si ton initial est rejeté,


00:42:49

Fabien Riou: Retombe dans la transmettre. Voilà,
Ludovic Lelievre: tu es obligé de le tu es obligé de le renvoyer
Fabien Riou: il retombe là-dedans.
Audric Podmilsak: Bah si
Fabien Riou: Recheté,
Paul Sorrentino: je
Fabien Riou: il est toujours en projet de rectificatif quoi.
Audric Podmilsak: ton
Fabien Riou: Il est toujours en projet.
Paul Sorrentino: si
Fabien Riou: C'est encore à à rectifier parce que tu as des erreurs, tu as des erreurs, il est rejeté, il est pas dans historisé, il est pas
Audric Podmilsak: Ouais, il faudrait une nouvelle colonne pour rejeter.
Fabien Riou: accepté.
Paul Sorrentino: parce que l'initial c'est pas gênant en fait. S'il est rejeté par les DGFIP, il est quand même en historique en rejeté. Et c'est vrai, c'est factuellement vrai, c'est que tu as pas transmis ton reporting parce qu'il a été rejeté. Dans le cadre d'un correctif, tu vas enlever l'ancien reporting, tu vas voir le nouveau à l'état rejeté, mais ce que tu vas pas voir, c'est que la DGFIP a quand même ton ancien reporting comme étant accepté, tu vois.


00:43:36

Audric Podmilsak: alors c'est pas tout à fait vrai parce que tu peux aller dans ton historique et savoir qu'il y avait une période initiale. qui elle a été acceptée. Donc tu as quand même l'information,
Paul Sorrentino: Ouais.
Audric Podmilsak: tu elle est elle est elle est un peu cachée. Par contre,
Paul Sorrentino: OK.
Audric Podmilsak: je pense que je pense que en fait dans historique mettre les rejetés dans historique, je suis pas sûr que soit une bonne idée. C'estàd que je pense qu'ici il faudrait transmettre un historique de accepter
Fabien Riou: Ouais
Audric Podmilsak: entre guillemets et un historique de et et des rejetés, tu vois,
Paul Sorrentino: Ok.
Audric Podmilsak: à
Fabien Riou: erreur là-dessus hein. Il y a que des accepter ici point. Il y a même pas de il y a même pas de Il y a même pas.
Audric Podmilsak: part.
Fabien Riou: Ouais oui en effet je pour enlever de toute façon il y a pas de rejeté ici. Les rejetés ils apparaissent dans un transmettre obligatoirement à rectifier à rejeter. Bon faudra finer ça en effet.


00:44:15

Fabien Riou: Là, je l'ai mis, ça s'est mis là. Mais et ici, il y a que des acceptés, quoi. Que des acceptés euh obligatoires.
Audric Podmilsak: Et par contre
Ludovic Lelievre: Mais du coup là les seuls rejets qu'on peut avoir,
Fabien Riou: Bah même
Ludovic Lelievre: c'est les rejets de CG. Jedim parce que parce que les rejets de la du PPF c'est c'est
Fabien Riou: pas euh
Ludovic Lelievre: Jedim qui les gère.
Paul Sorrentino: Ah bon
Fabien Riou: Ouais,
Paul Sorrentino: ?
Fabien Riou: ouais. Mais alors du coup, il y a rien à faire
Ludovic Lelievre: Donc il il resterait en transmis sans que parce que du coup si ça passe les schéma tron
Fabien Riou: de
Ludovic Lelievre: ben c'est censé être accepté par le par le PPF et si le PPF accepte pas c'est qu'il y a une une couille quelque part côté PPF et ça c'est Jim de gérer
Audric Podmilsak: Oui. Donc on est
Ludovic Lelievre: ça.
Fabien Riou: Ouais.
Paul Sorrentino: Ils font aucun check de leur côté.


00:44:56

Paul Sorrentino: P.
Ludovic Lelievre: Ils sont des checks, mais Du coup, comme ils nous ont donné les schémas tron officiels, bah si on passe les schémas officiels et que ça fonctionne bien,
Paul Sorrentino: Ouais.
Ludovic Lelievre: ben si ça pète côté PPF,
Paul Sorrentino: OK.
Audric Podmilsak: et et techniquement même les rejets CG,
Ludovic Lelievre: ben
Fabien Riou: Ouais.
Audric Podmilsak: on n pas censé en avoir parce qu'en fait vu qu'on joue le schéma en amont en fait c'est on est vraiment sur des on se casse tête pour des cas vraiment edge quoi.
Ludovic Lelievre: Ouais.
Paul Sorrentino: Ok.
Ludovic Lelievre: Oui.
Audric Podmilsak: Donc je pense que c'est acceptable de les cacher comme tu dis dans l'historique dans ce cas-là quoi.
Fabien Riou: Ouais. Bon
Ludovic Lelievre: OK.
Audric Podmilsak: parce que moi plus on avance plus ça me switch ma façon de voir le truc c'est que nous en fait ce qui nous intéresse c'est vraiment des périodes de
Fabien Riou: bre
Audric Podmilsak: reporting et qu'une période de reporting en gros va porter le fait queil y a eu une déclaration ou n déclaration


00:45:38

Audric Podmilsak: corrective
Ludovic Lelievre: Oui, mais c'est euh Oui, c'est qu'est-ce que qu'est-ce qu' a l'administration fiscale fiscale pour en TVA pour pour cette entreprise et cette
Fabien Riou: Yeah.
Audric Podmilsak: pour cette période.
Ludovic Lelievre: période?
Paul Sorrentino: Hm.
Ludovic Lelievre: Ouais. OK. OK. OK. Donc au moment au moment où on bascule de un rectificatif, au moment où on transmet un rectificatif, il prend la place de l'ancienne période s'il y en a une.
Audric Podmilsak: Go!
Ludovic Lelievre: OK.
Fabien Riou: Hm.
Ludovic Lelievre: En terme de euh si tu rebascules Fabien sur le euh sur le notion.
Fabien Riou: Ouais.
Ludovic Lelievre: Du coup, ce qu'on se dit si tu descends mais tu es noté plan d'actionou il y a une pour moi il y a une une step zéro où aujourd'hui on côté vente on gère mal les rectificatifs dans le sens où on les empêche pas et il faudrait qu'on se backup de ça de la même manière qu'on empêche les factures hors période côté qui viennent de AP parce qu'aujourd'hui si il y a rien qui empêche un client de nous envoyer une facture de vente via la public API dans le passé et nous on va créer un rectificatif une période initiale avec une due date qui va jamais se qui va jamais s'envoyer


00:47:13

Ludovic Lelievre: et donc ça c'est le premier point et idem sur la partie E-reporting de vente
Audric Podmilsak: Ok.
Ludovic Lelievre: Euh une fois qu'on a transmis le reporting et ben on a toujours le bouton de création de de transaction B2C une fois que le le reporting est transmis. Donc ça c'est un peu le une brique à part que j'ai mise sur tant qu'on n pas le toute cette logique de reporting qui fonctionne sur les ventes, il faut qu'on empêche l'import de ces factures de la même manière qu'on l'empêche côté AP.
Audric Podmilsak: Alors côté AP, on n'empêche pas,
Ludovic Lelievre: Oui,
Audric Podmilsak: on on traite ce qui est Voilà,
Ludovic Lelievre: on les met en erreur.
Audric Podmilsak: je tiens un président nuance parce qu'on peut rien empêcher côté AP d'ailleurs. On est on est ils ont ils ont ils nous ont émis la volonté de se désolariser de nous en fait de pas être responsable de ça.
Ludovic Lelievre: Oi.
Audric Podmilsak: Nous, ils vont nous dire il y a ces factures là et c'est nous qui viendrons les récupérer. On va changer, on va inverser la la dépendance ici à terme.


00:48:07

Audric Podmilsak: Mais euh l'idée c'est que donc du coup nous la façon dont on les traite à l'heure actuelle c'est si c'est hors période on touche pas.
Ludovic Lelievre: Ouais. du coup de de faire la même logique côté vente. Si on reçoit une facture de vente hors période,
Audric Podmilsak: Ouais.
Ludovic Lelievre: on la met en erreur tant qu'on n' pas euh toute cette brique de reporting rectificatif fonctionnel sur la
Audric Podmilsak: Et et c'est pour ça du coup que moi je pense que ça peut être prévu dans un second temps.
Ludovic Lelievre: vente.
Audric Podmilsak: Je pense qu'il faut il faut se focus je dirais moi sur le channel achat et donc du coup AP euh et faire le bout en bout pour le le cas AP. ça m'a l'air d'être plus simple mais après
Ludovic Lelievre: Oui, mais du coup cette step zéro, elle nous protège sur des imports qui arriveront entre
Audric Podmilsak: Euh
Ludovic Lelievre: maintenant comme on va se focaliser sur le sur AP en premier lieu de se dire"OK, on est au moins on est safe côté vente parce que on a cette brique qui mettra tous ses flux en erreur et donc on peut attendre, on peut comme ça, on évite de se retrouver avec des du reporting qui vient qui qui sera pollué par des imports qu'on g qu'on ne gère pas aujourd'hui.


00:49:12

Ludovic Lelievre: Mais ça je pense que c'est tout petit. C'est pour ça je mis un step zéro. Comme ça ça on bloque la partie vente et comme ça step 1 on se focalise côté côté AP et on déroule le donc les scénarios d'ajout de modification et de suppression et on va jusqu'à le fait de pouvoir envoyer ce rectificatif manuellement. Donc on fait tout le tout le flow qu'on s'est dit sur la sur cette brique sur les flux qui viennent de
Audric Podmilsak: OK. Et làdedans dans la modification,
Ludovic Lelievre: AP.
Audric Podmilsak: on garde euh la modification qui change la période ou on l'exclut ça aussi?
Ludovic Lelievre: C'est quoi la modification qui change la période? Ah la l'interpériode euh j'ai mis step Ouais,
Audric Podmilsak: Bah si par contre tu es
Ludovic Lelievre: j'ai mis step 6 modification interpériode. Je je l'ai mis loin.
Audric Podmilsak: OK. Et comment tu bloques ça? Du coup, ça veut dire
Ludovic Lelievre: Ouais.


00:50:03

Ludovic Lelievre: Et du coup c'est il nous faut une nouvelle règle. Il nous faudrait une nouvelle règle ici où on bloque euh
Audric Podmilsak: que
Ludovic Lelievre: reporting euh d'achat, on bloque les euh modifications de euh
Audric Podmilsak: c'est dans la step 1 du coup. Mais mais moi je pense tu le mets sous ton 1.2 parce qu'en fait ça c'est valable que si tu es déjà capable de faire du reporting parce que là
Ludovic Lelievre: Ouais,
Audric Podmilsak: en l'état on bloque déjà donc c'est en 1 1.2 de en dessous tuas un truc détaillé ou je sais pas
Ludovic Lelievre: c'est ça.
Paul Sorrentino: M.
Ludovic Lelievre: modification, on bloque on bloque les modifications de
Audric Podmilsak: comment
Ludovic Lelievre: facture hors période.
Audric Podmilsak: les changements de quand même période de date.
Ludovic Lelievre: On bloque les les modifications de date de date de
Audric Podmilsak: Ouais. Ouais. Du coup,
Ludovic Lelievre: facture.
Audric Podmilsak: c'est c'est la date et c'est le sirène aussi


00:50:54

Ludovic Lelievre: Pourquoi on peut changer?
Audric Podmilsak: parce que la clé d'une période, c'est le sirène et la date la le sirène du
Ludovic Lelievre: Ah oui,
Audric Podmilsak: du de le sirène de du
Ludovic Lelievre: OK. Ouais,
Audric Podmilsak: vendeur.
Ludovic Lelievre: ça marche. Ouais. Du coup, on a ça et et du coup dans cette step 1, on aurait cette logique de à la fois création d'un reporting rectificatif sans sans période transmise et avec période transmise.
Audric Podmilsak: Ouais.
Ludovic Lelievre: Et on déroulerait ça dans les quatre dans les trois cas, le l'ajout, la modification et la suppression.
Audric Podmilsak: Ouais, je pense ça fait déjà un beau bébé avec avec toute la complexité sur la partie 8.
Ludovic Lelievre: On pourrait commencer par ça et ensuite bah ensuite faudrait dérouler ça sur les flux qui viennent de la public API et ensuite sur tout ce qui est source manuelle. Donc tu es dans un rectificatif déjà transmis et tu peux supprimer ou modifier une trans ou ajouter une transaction B2C ou euh supprimer une facture
Fabien Riou: p*****
Ludovic Lelievre: de vente.


00:52:04

Fabien Riou: !
Ludovic Lelievre: Est-ce que cette step 3 vous la sortirez dans Je pense que c'est comme ça on se focalise par source. On a une source, on gère tout ce qui vient de AP, on gère tout ce qui vient de la public API et ensuite on gère ce qui euh ce qui vient d'action
Audric Podmilsak: Ouais.
Ludovic Lelievre: manuelle.
Audric Podmilsak: Quitte à ce que sur la partie bac, on avance déjà sur la step 2 alors que la step 1, on a encore sur une partie. Je pense que la step 1 côté bac, elle est plus simple. Par contre, côté fonte, euh, elle embarque énormément de choses.
Paul Sorrentino: Ah oui et non parce que la step 1 c'est le bootstrap du rectificatif côté bac aussi donc c'est la création des
Audric Podmilsak: Euh,
Paul Sorrentino: objets en tant que tel enfin la création du schéma de données et cetera c'est je pense que elle est elle est balaise Si
Audric Podmilsak: c'est pas faux. Mais oui, du coup ça fait en tout cas la step 1 fait déjà un morceau assez balaise.
Paul Sorrentino: euh
Audric Podmilsak: Donc c'est bien de le faire comme ça et après de se faire source par source.


00:53:05

Ludovic Lelievre: OK, j'ai mis du coup là-dessus la partie sur laquelle j'ai je sais pas trop quand la mettre,
Audric Podmilsak: Euh
Ludovic Lelievre: c'est toute la partie comparaison parce que on peut vivre on peut on peut avoir une step 1 qui a qui va jusqu'à l'envoi du rectificatif sans faire de comparaison avec le le reporting précédent et avec cette notion de tag.
Paul Sorrentino: M.
Audric Podmilsak: ouais.
Ludovic Lelievre: Donc c'est c'est cette partie-là que j'aimerais qu'on qu'on ait une bonne visibilité sur la complexité et ne pas se dire que on utilise tout notre temps de septembre à
Fabien Riou: aut
Audric Podmilsak: M.
Ludovic Lelievre: vouloir faire cette comparaison dans l' step 1 et du coup ça repousse la step 2 et l' stepp 3 qui mettrait à risque du coup des potentielles rectifications sur de des factures de vente pour de l'optimisation Uh.
Fabien Riou: M.
Ludovic Lelievre: de lui côté côté rectificatif, sachant qu'ensuite ensuite ça sera toujours,
Paul Sorrentino: M.
Ludovic Lelievre: j'imagine cette même logique qui sera appliquée dans l'ensemble des rectificatifs pour venir taguer la
Paul Sorrentino: Je sais pas si on va gagner tant que ça en enlevant la l'aspect comparatif puisqu'il faut quand même de toute


00:54:10

Ludovic Lelievre: facture.
Paul Sorrentino: façon le faire d'un point de vue logique pour pouvoir être capable d'envoyer le rectificatif. Il faut que de base on compare avec l'ancien.
Ludovic Lelievre: Ok.
Paul Sorrentino: Si tu supprimes une facture le rectificatif il faut qu'il 100 facture il faut qu'il en envoie 99. Donc dans tous les cas, le rectificatif il est enfin comparatif, il est il est fait le du simple fait de devoir l'envoyer.
Ludovic Lelievre: Ouais.
Paul Sorrentino: Après, c'est du gain en nuille,
Ludovic Lelievre: OK.
Paul Sorrentino: mais je suis pas sûr d'être le boulot d'anglement là-dessus.
Audric Podmilsak: Bah par contre,
Paul Sorrentino: Donc
Audric Podmilsak: je pense que postponé dans le 1 en 1.4 4 le le le le dip, tu vois, et l'avoir dans une US à part.
Paul Sorrentino: euh
Audric Podmilsak: Ça c'est intéressant parce qu'en fait ça fait un petit bout en moins à chiper,
Ludovic Lelievre: Ok.
Audric Podmilsak: tu vois. Et on peut dire qu'on chipe une première version où on envoie l'état actuel et euh après


00:54:55

Ludovic Lelievre: Ok.
Audric Podmilsak: on fait une on on peut chipper ça. Enfin, je sais pas mais à à voir comment est-ce qu'on les goupie, mais ça peut être intéressant de de le splitter en US à part à minima. Par contre, je rejoins Paul, je pense qu'il y a pas en fait, ça dépend du dif. Moi, je serai d'avis de faire le dif juste du tag, modifier, supprimer,
Paul Sorrentino: Oui, voilà.
Audric Podmilsak: euh ajouter,
Paul Sorrentino: Hm.
Audric Podmilsak: et d'avoir un mode dégradé sur le modifier pour commencer
Paul Sorrentino: Que le modifier. Ouais,
Fabien Riou: OK.
Paul Sorrentino: on a aucune info. On voit juste modifier
Fabien Riou: Ouais.
Paul Sorrentino: point.
Fabien Riou: Ouais.
Audric Podmilsak: et vraiment ce ce focus sur modifier uniquement tout ça, c'est fini parce que la rigueur c'est pas parce qu'on peut aller loin effectivement sur modifier. Ou là ou là ou là ou là support
Ludovic Lelievre: Euh parfait. Ben du coup euh on a on a les briques qu'il nous faut pour pour avancer et segmenter le ce projet.


00:56:01

Fabien Riou: Ouais,
Ludovic Lelievre: Merci.
Paul Sorrentino: Il a une belle bête encore.
Ludovic Lelievre: Ouais.
Fabien Riou: c'est une belle bête.
Paul Sorrentino: Ouais.
Audric Podmilsak: et et on on est d'accord que ça c'est objectif c'est euh si ça chiffre au Au final, c'est pas non plus dramatique pour les clients parce qu'ils peuvent faire leur correctif après coup. Mais mais
Ludovic Lelievre: Ouais, sachant que on a d'autres éléments,
Audric Podmilsak: c'est
Ludovic Lelievre: mais ça on pourra voir ça demain parce que là faut que j'enchaîne avec une autre rue, mais il y a d'autres d'autres trucs pour cet endroit aussi.
Audric Podmilsak: Ouais.
Ludovic Lelievre: Donc donc ça sera à mettre sur parce qu'on a dans dans le reporting aujourd'hui,
Audric Podmilsak: OK.
Ludovic Lelievre: il nous il nous manque des briques, il nous manque le le reporting de paiement en initial qui lui est un tout petit peu prioritaire plus prioritaire que le rectificatif puisque il arrivera avant, on peut dire au client bah ton rectificatif désolé mais tu l'envoies pas en septembre, tu l'envoies en octobre ou en ou en novembre.


00:56:50

Ludovic Lelievre: Et le dernier truc c'est le le le les reportings à partir de flufr.
Audric Podmilsak: Attends attends attends attends les reporting. Ah pousser des flux fer directement.
Ludovic Lelievre: Ouais. Que le client nous pousse un flux frr pour
Audric Podmilsak: Ça c'est pas ça. Ah
Ludovic Lelievre: pour dans la public au lieu de nous nous pousser des factures B2 bien to B2C et nous on
Audric Podmilsak: ok.
Ludovic Lelievre: construit à partir de ça qui nous pousse le flux FRR.
Audric Podmilsak: Ah ça dépend en fait à quel point ça peut être pas cher hein. C'està dire que tu peux pousser le transmettre un CVIM. Ça dépend à quel point tu veux avoir une nuit euh léchée dessus
Ludovic Lelievre: Non non, bah ça c'est le moins du possible hein. C'est juste le techniquement savoir le faire,
Audric Podmilsak: quoi.
Ludovic Lelievre: pouvoir dire pouvoir avoir la période qui s'affiche avec à l'intérieur je pense un un nouveau tab qui serait FRR et là on aurait ce le flux FRR qui a été poussé pour cette période. Mais bon, c'est c'est quand même c'est quand même un petit un du boulot.
Audric Podmilsak: OK.
Ludovic Lelievre: Donc il y a ça, il y a ça, on pourra en reparler demain mais c'est les deux les deux les deux sujets plus prioritaires sur ce reporting rectificatif de savoir le de faire l'initial de paiement et l'initial de via du FRR. Voilà. Voilà.
Audric Podmilsak: Cool.
Ludovic Lelievre: Merci à vous.
Fabien Riou: Allez top.
Paul Sorrentino: Merci,
Ludovic Lelievre: À plus.
Paul Sorrentino: bon courage.
Fabien Riou: On met tout ça propre.
Ludovic Lelievre: plus propre.
Paul Sorrentino: Allez
Fabien Riou: Ouais, trop bien.
Paul Sorrentino: ciao.
Audric Podmilsak: à plus.
Paul Sorrentino: On change de on repasse sur le myth pourir le transcript.
Audric Podmilsak: Ouais, vas-y, vas-y,


Transcription terminée après 00:58:32

Cette transcription modifiable a été générée par ordinateur et peut contenir des erreurs. Les utilisateurs peuvent également modifier le texte après sa création.
