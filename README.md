# criminau.xyz

Blog Simple.

En savoir plus :   <https://criminau.xyz/apropos/>


[![Netlify Status](https://api.netlify.com/api/v1/badges/f6104326-809a-4b92-8914-4a7a34467c5c/deploy-status)](https://app.netlify.com/sites/criminau-site/deploys)


## Prochaine version

### V.02.9

- [X] correction article (+PDF)
- [X] clear and developp cover and sky-cover.
- [X] archetypes default.md
- [ ] cleaning pagination + new one (homepage) (à vérifier)
- [ ] SEO width and weight of image. ??
- [ ] .Params.image ??
- [ ] clear markdown syntax
- [ ] css page de texte
- [ ] css page d'accueil (à vérifier)
- [ ] responsive footer. (à vérifier)
- [ ] responsive button footer (à vérifier)
- [ ] responsive nav. (à vérifier)
- [ ] introducart (à vérfier)
- [ ] responsive home-info (à vérifier)
- [X] home-info.html
- [ ] font-size (em) + css (en cours)
- [ ] bouton partager. section "partage" !
- [ ] iteroni vidéo iframe
- [ ] nitter tweet iframe ? citation.
- [ ] Opt out FLoC ??
- [X] préparation des thèmes, tags et séries.
- [ ] préparation section : note ?
- [X] Retour en haut de la page, optimisation et esthétique. (à vérifier + seo)
- [ ] cache policy maj (à vérifier)
- [ ] css mobile (homepage+page de texte+searchpage with term.
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