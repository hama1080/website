---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: single
classes: wide
title: "インストールする際の前提条件"
permalink: /docs/install-and-update/prerequisite
sidebar:
  nav: "docs"
---
* 全てのマシンがAMD64(Intel 64bit CPU)である必要があります
* OSは Ubuntu Server 18.04 または NVIDIA DGX OS 4 になります
* 全てのマシンに共通のアカウントでsshログインできるようにします
  * そのアカウントが全てのマシンでsudoできるようにします
  * sshキーを使用する場合は、id_rsaファイルを構築ツールを実行するマシンの/root/.ssh/に所有者root、パーミッション0600で配置します。ペアのid_rsa.pubも同様に配置します
    * 構築に利用するツールdeepopsがid_rsa.pubの配布を行います。既にsshキーを配布済みでもこのプロセスが起きるため、id_rsa.pubが存在しないとエラーになります
* 用意したマシンの名前解決と時刻同期を出来るようにします。
  * DNSとNTPを使うことが推奨です
* 各マシンがインターネットアクセス出来るようにします。
* nvidia-docker・GPUドライバ・dockerがインストール済みの環境では競合が起きる可能性があるため、アンインストールを推奨します
  * 特に、`/etc/apt/sources.list.d/`配下にnvidia-dockerやGPUドライバ、dockerのリポジトリ登録を独自に用意している場合、そのソフトウェアをアンインストール後に`/etc/apt/sources.list.d/`の対応するファイルを削除することを推奨します
* swapはオフにします