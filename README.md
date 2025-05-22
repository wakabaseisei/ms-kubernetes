# ms-kubernetes

このリポジトリは、MSプロジェクトにおける **KubernetesマニフェストをGitOpsで一元管理** するためのリポジトリです。  
ArgoCDを通じてマイクロサービス群を管理し、**環境ごとに明確に分離された構成と再現性ある運用**を実現しています。

---

## 🧩 概要

- **GitOps運用:**  
  ArgoCDの `ApplicationSet` を利用して、サービスごとのHelmチャートを自動的に登録。  
  変更内容はArgoCD上で検知され、**手動でSync操作を行うことで反映**されます。

- **環境分離:**  
  各サービスごとに `dev` / `prod` の `values.yaml` を用意し、明確な環境分離を実現

- **共通テンプレート:**  
  各マイクロサービスで再利用可能なHelmテンプレートを整備し、構成の統一性を担保

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
| GitOps           | ArgoCD (ApplicationSet)     | Helmテンプレートでサービスを登録・管理         |
| マニフェスト管理 | Helm                        | DRYな構成、共通パターンをテンプレート化して管理 |
| デプロイ対象     | Kubernetes (EKS)            | Deployment/Ingress/Service等をHelmで定義       |

---

## 📄 備考

- `platform/` 配下の ApplicationSet により、`services/` 配下の全サービスが ArgoCD に自動登録されます
