# completely_understood

| モノ                               | どういうことができるか                       | 主観メモ                                                  |
| ---------------------------------- | -------------------------------------------- | --------------------------------------------------------- |
| resmonio/kubernetes_event_exporter | K8s Eventsを読み込んで外部に連携する         | layout等も設定できるので使いやすい                        |
| vmware-archive/eventrouter         | K8s Eventsを読み込んで外部に連携する         | Archivedなので今後は利用しない                            |
| robusta-dev/kubewatch              | K8s Resourceの生成などの情報を外部に通知する | 単体ではstdout出力できないので、Robusta Runnnerを利用する |
|                                    |                                              |                                                           |