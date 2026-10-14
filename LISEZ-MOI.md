# Ajout au dépôt 1bhih1-downloader : import des playlists Spotify (sans compte, pour tout le monde)

À ajouter dans **KalbouzGalactik/1bhih1-downloader** : Add file → Upload files, glisse le dossier `.github` et le dossier `scripts`, puis Commit.
Remplace les fichiers de la version précédente. Rien à changer dans Cloudflare (`DL_REPO` et `DOWNLOAD_TOKEN` suffisent). **Les élèves n'ont rien à faire.**

## Comment ça marche
Sur le site : Musique → Importer → lien Spotify → **Playlist complète**. Le workflow essaie, dans l'ordre :
1. (facultatif) l'API officielle avec ton compte, si tu as créé les secrets `SPOTIFY_CLIENT_ID` + `SPOTIFY_REFRESH_TOKEN` (Paramètres → Spotify · administrateur) : tes playlists ;
2. **sans compte**, comme le fait le lecteur web de Spotify (module SpotifyScraper) : n'importe quelle playlist *publique*, y compris celles des élèves ;
3. la page publique de Spotify : 100 titres au maximum.
Ensuite chaque titre est cherché sur YouTube Music (durée ±3 s, ni live ni remix) et les liens reviennent dans le site.

## Pourquoi cette méthode
Depuis février 2026, l'API officielle de Spotify ne donne la liste complète qu'au propriétaire ou aux collaborateurs d'une playlist,
et une application n'accepte que 5 comptes. C'est impossible pour une classe : on passe donc par la lecture publique, sans compte.

## Limites (à lire)
- La méthode 2 n'est **pas une API officielle** : Spotify peut la changer sans prévenir. Le module est maintenu et testé chaque jour par son auteur ;
  s'il casse, il suffit en général de relancer plus tard ou de mettre le module à jour (le workflow prend toujours la dernière version).
- La playlist doit être **publique** (Spotify → ⋯ → ajouter au profil / rendre publique).
- Si la méthode 2 échoue, le site reçoit 100 titres et affiche la raison exacte.
