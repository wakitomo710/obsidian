ホストPCと仮想マシンがファイルを共有

- dfコマンドでshareがあるかチェック
- sudo mkdir [mount point]
- sudo mount -t 9p -o trans=virtio share [mount point] -oversion=9p2000.L

share	[mount point]	9p	trans=virtio,version=9p2000.L,rw,_netdev,nofail	0	0
[UTM　MacにUbuntu入れた後、共有ディレクトリの設定方法 #UTM - Qiita](https://qiita.com/keitean/items/1979a6dc2424c1d696ef)