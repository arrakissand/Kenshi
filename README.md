<h1 align="center">Kenshi</h1>

> Süresi belli değil - diğer nodlarınızla yanyana kurabilirsiniz.

> Ödül top 200'e - ödüller sadece en iyi performansı veren nodlara dağıtılacak.

> TOPLULUK KANALLARI: [Sohbet Kanalımız](https://t.me/RuesChat) - [Duyurular ve Gelişmeler](https://t.me/RuesAnnouncement) - [Whatsapp](https://whatsapp.com/channel/0029VaBcj7V1dAw1H2KhMk34) - [SandWorm telegram](https://t.me/arrakissand) - [Kenshi Telegram](https://t.me/KenshiTech)

#

<h1 align="center">Donanım</h1>

> Bir cihaz temin etmedim mevcut nodeların yanına kurdum - ario, santiment, voi yanlarında denedim problem olmadı.

> top 200'de olmak için en önemli kriter internet olacak, [Hetzner](https://hetzner.cloud/?ref=gIFAhUnYYjD3) kullandım.

> illa temin edilecekse 2 CPU 2 RAM ideal 'şimdilik'

#

<h1 align="center">Kurulum</h1>

```console
# sunucu güncelleme
sudo apt update -y && sudo apt upgrade -y

# burada 20 ve 60 saniye bekliyoruz
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -

# komutları sırasıyla girelim:
sudo apt-get install -y nodejs
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
nvm install 16
nvm use 16
apt install npm
sudo npm i -g @kenshi.io/unchained
sudo npm i -g @kenshi.io/unchained@latest
```

<h1 align="center">Yapılandırma işlemleri ve başlatma</h1>

```console
# conf.yaml içine girelim
sudo nano conf.yaml

# burada sadece SandWorm kısmını kendi adınız yapın
log: info
name: SandWorm
lite: true
gossip: 5
rpc:
  ethereum:
    - https://ethereum.publicnode.com
    - https://eth.llamarpc.com
    - wss://ethereum.publicnode.com
    - https://eth.rpc.blxrbdn.com
database:
  url: mongodb+srv://<user>:<password>@<url>/?retryWrites=true&w=majority
  name: unchained

> CTRL X Y Enter ile çıkıyoruz.


# Screen içine girelim
screen -S kenshi

# Başlatalım
unchained start conf.yaml --generate

> CTRL A D ile screenden çıkıyoruz.

# Notlar:
> Son komuttan sonra loglar akmaya başlayacak ve sync olmaya başlayacaksınız
> 5 dakikada bir gözüken Leaderboard'da siz OLMAYACAKSINIZ
> Bu leaderboard - sizin node'larınız tarafından diğer nodelara verilen puanlardır
> Sizde başkaların nodelarından puan alacaksınız, ödül nodlar arası iletişim hızına ve erişime dayalıdır - hetzner'iniz varsa kafanız rahat olabilir.
> Node u restart etmek zorunda kalırsnız '--generate' opsionunu kaldırın. Yoksa sistemi yeni bir node olarak algılar.
```

> conf.yaml içinde ki secret key önemli, `cat conf.yaml` komut ile çıktıyı kaydedebilirsiniz.

> Sistemi [burada](https://charts.mongodb.com/charts-unchained-gpust/public/dashboards/cbb6ccf6-15b2-4187-be56-ff9d2e25a48a) kontrol edebilirsiniz. Henüz kendi nodunuzun sırlaması nasıl görünecek belli değil.

