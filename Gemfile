# ⚠️ Ce Gemfile ne sert QU'AU `bundle exec` local (§5 de la spec).
#
# Le builder GitHub Pages classique utilise son PROPRE environnement épinglé et
# ignore ce fichier. La gem `github-pages` est ici pour rapprocher le local du
# distant — notamment jekyll-sass-converter 1.5.2 (libsass), qui échoue sur un
# terme additif dans clamp() sans calc().
#
# ⚠️ Construire en local ne prouve RIEN sur le distant : en safe mode, un plugin
#    non whitelisté est ignoré SANS ERREUR. La seule preuve est le build GitHub.

source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

# Vérification des liens (critère §6). Hors du build.
gem "html-proofer", "~> 5.0", group: :test
