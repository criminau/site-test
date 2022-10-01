# criminau.xyz

Blog Simple.

En savoir plus :   <https://criminau.xyz/apropos/>


[![Netlify Status](https://api.netlify.com/api/v1/badges/f6104326-809a-4b92-8914-4a7a34467c5c/deploy-status)](https://app.netlify.com/sites/criminau-site/deploys)


## Prochaine version

### V.02.9

- [X] correction article (+PDF)
- [X] correction, développement et optimisation (html+css) cover and sky-cover.
- [X] archetypes default.md.
- [X] nettoyage (code+css) pagination + une en haut de la page d'accueil.
- [X] SEO width and weight of image.
- [X] Retour en haut de la page, optimisation et esthétique.
- [X] cache policy (90j).
- [X] css page d'accueil.
- [X] responsive footer.
- [X] responsive button footer.
- [X] responsive nav.
- [X] introducart.
- [X] responsive et correction du html home-info.
- [X] responsive search.
- [X] préparation des thèmes, tags et séries.
- [X] vimeo responsive shortcode + youtube work.

- [ ] .Params.image ??
- [ ] clear markdown syntax
- [ ] css page de texte
- [ ] css archives (à vérifier)
- [ ] font-size (em) + css (en cours)
- [ ] bouton partager. section "partage" !
- [ ] iteroni vidéo iframe
- [ ] nitter tweet iframe (nitter n'autorise pas la connexion)
- [ ] Opt out FLoC ??
- [ ] s'engager dans les outils de recherche et d'affichage des taxonomies
- [ ] préparation section : note ?
- [ ] site responsive avec css mobile (720/1320)
- [*] schema article : author + image(ok) + headline. post single. [A confirmer]
-- image (ok)
<meta itemprop="image" content="/some/url/to/an/image.gif" /> (si besoin)
-- author (ok)
-- headline(titre) (ok)
- [ ]
- [ ] clear css (end)
- [ ] clear html (en cours)


- homepage : affichage des catégories mais pas des tags ? oui CSS
Thèmes -> categories


un grand caré (post-entry), dedens on y fou 2 carré &mg a guahce et 1 a droite texte. on y fou img a gauche le reste a droite. double carré avec x3 dedans.

https://cloudcannon.com/community/learn/hugo-tutorial/taxonomies/
title: My Blog Post
categories: [development, publishing]
tags: [hugo,content,static site generator]


.Site.GetPage for Taxonomies

Because taxonomies are lists, the .GetPage function can be used to get all the pages associated with a particular taxonomy term using a terse syntax. The following ranges over the full list of tags on your site and links to each of the individual taxonomy pages for each term without having to use the more fragile URL construction of the “List All Site Tags” example above:
links-to-all-tags.html

{{ $taxo := "tags" }}
<ul class="{{ $taxo }}">
    {{ with ($.Site.GetPage (printf "/%s" $taxo)) }}
        {{ range .Pages }}
            <li><a href="{{ .Permalink }}">{{ .Title}}</a></li>
        {{ end }}
    {{ end }}
</ul>



layouts/partials/all-taxonomies.html

<section>
    <ul id="all-taxonomies">
        {{ range $taxonomy_term, $taxonomy := .Site.Taxonomies }}
            {{ with $.Site.GetPage (printf "/%s" $taxonomy_term) }}
                <li><a href="{{ .Permalink }}">{{ $taxonomy_term }}</a>
                    <ul>
                        {{ range $key, $value := $taxonomy }}
                            <li>{{ $key }}</li>
                            <ul>
                                {{ range $value.Pages }}
                                    <li hugo-nav="{{ .RelPermalink}}">
                                        <a href="{{ .Permalink}}">{{ .LinkTitle }}</a>
                                    </li>
                                {{ end }}
                            </ul>
                        {{ end }}
                    </ul>
                </li>
            {{ end }}
        {{ end }}
    </ul>
</section>

Actor                    <- Taxonomy
    Bruce Willis         <- Term
        The Sixth Sense  <- Value
        Unbreakable      <- Value
        Moonrise Kingdom <- Value
        
    {{ range (.GetTerms "tags") }}
    <li><a href="{{ .Permalink }}">{{ .LinkTitle }}</a></li>
    {{ end }}