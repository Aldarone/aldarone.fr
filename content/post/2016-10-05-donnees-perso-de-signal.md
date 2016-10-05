+++
comments = true
date = "2016-10-05T08:14:05+02:00"
image = "/img/archive-register.jpg"
slug = "les-donnees-personelles-enregistrees-par-signal"
title = "Les données personnelles enregistrées par Signal"

+++

Début 2016, OpenWhisper Systems a été contraint de fournir à la justice américaine les informations personnelles qu'ils possédaient sur deux utilisateurs de Signal.

Dans une volonté de transparence, l'organisme a également fait le nécessaire pour pouvoir publier les échanges qu'ils ont eu ainsi que les informations (anonymisées) qu'ils ont du fournir.

C'est donc l'occasion pour nous de prendre connaissance de l'ampleur des données récoltées par Signal.

En effet, ses détracteurs évoquent régulièrement la dépendance de l'application au service de push de Google pour conclure que Signal est une passoire à méta-données et que pour être vraiment à l'abri il vaudrait mieux utiliser Silence.

Pour rappel, Silence utilise les SMS. Les méta-données associées à chaque messages sont donc identiques aux SMS non chiffrés ce qui signifie que les messages envoyées par Silence sont visibles sur la facture détaillée de votre abonnement.

De son côté Signal utilise une connexion TLS et affirme n'enregistrer que le strict minimum pour le fonctionnement du service. Ce qui est à présent prouvé puisque les seules informations fournies à la justice sont :

![Data provided by Open Whisper Systems: Last connection date and account creation date](/img/signal-subpoena-data.png)

- La date de création du compte.
- La date de dernière connexion au service.

Et c'est tout.

Une section nommée « [Big Brother][1] » a également été créee pour contenir les futur compte rendu des demandes de la justice.

Silence conserve comme seul avantage que le transport SMS est toujours plus fiable en France que le transport data, mais on a à présent la certitude que Signal protège bien plus efficacement notre vie privée.

[1]: https://whispersystems.org/bigbrother/
