# ms-kubernetes

このリポジトリは、MSプロジェクトにおける **KubernetesマニフェストをGitOpsで一元管理** するためのリポジトリです。  
ArgoCDを通じてマイクロサービス群を自動デプロイし、**環境ごとに明確に分離された構成と継続的な反映**を実現しています。

---

## 🧩 概要

- **GitOps運用:**  
  ArgoCDの `ApplicationSet` を利用し、サービスごとのHelmチャートを自動でデプロイ

- **環境分離:**  
  各サービスごとに `dev` / `prod` の `values.yaml` を用意し、明確な環境分離を実現

- **共通テンプレート:**  
  各マイクロサービスで再利用可能なHelmテンプレートを整備

---

## 📁 ディレクトリ構成

```
.
├── platform/ # ArgoCD ApplicationSet 定義（環境別）
├── services/ # 各サービスの Helm チャート管理
├── values/ # サービスごとの環境別 values.yaml
└── README.md
```


---

## 🛠 使用技術

| 分類             | 技術                        | 補足                                          |
|------------------|-----------------------------|-----------------------------------------------|
| GitOps           | ArgoCD (ApplicationSet)     | Helmテンプレートでサービスを自動展開           |
| マニフェスト管理 | Helm                        | DRYな構成、共通パターンをテンプレート化して管理 |
| デプロイ対象     | Kubernetes (EKS)            | Deployment/Ingress/Service等をHelmで定義       |

---

## 📄 備考

- `platform/` 配下の ApplicationSet により、`services/` 配下の全サービスが自動的に ArgoCD に登録されます
