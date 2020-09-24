---
title: 雲端原生應用程式套件組合
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式套件組合
ms.date: 05/13/2020
ms.openlocfilehash: 7f1fcd448f3299a31043bf269717f7b777329c62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158119"
---
# <a name="cloud-native-application-bundles"></a>雲端原生應用程式套件組合

雲端原生應用程式的重要屬性是，它們會利用雲端的功能來加速開發。 這種設計通常表示完整的應用程式會使用不同種類的技術。 應用程式可能會在 Docker 容器中運送，某些服務可能會使用 Azure Functions，而其他元件則可直接在使用硬體 GPU 加速配置於大型裸機伺服器上的虛擬機器上執行。 沒有兩個雲端原生應用程式相同，因此很難提供單一機制來傳送它們。

Docker 容器可以使用 Helm 圖表進行部署，以在 Kubernetes 上執行。 Azure Functions 可以使用 Terraform 範本進行配置。 最後，您可以使用 Terraform 來配置虛擬機器，但使用 Ansible 來建立。 這是一項完整的技術，而且沒有辦法將它們全部封裝成合理的封裝。 直到目前為止。

雲端原生應用程式套件組合 (CNABs) 是由許多志同道合的公司（例如 Microsoft、Docker 和 HashiCorp）共同作業，以開發將封裝散發的應用程式。

這項工作已在2018年12月宣佈完成，因此仍有相當多的工作要將精力公開給更大的群體。 不過，已經有開啟的 [規格](https://github.com/deislabs/cnab-spec) 和稱為 [Duffle](https://duffle.sh/)的參考實作為參考。 這項工具是以 Go 撰寫的，是 Docker 與 Microsoft 之間的共同工作。

CNABs 可包含不同種類的安裝技術。 這可讓 Helm 圖表、Terraform 範本和 Ansible 的工作手冊等專案並存于相同的套件中。 一旦建立之後，套件就會獨立且可攜;您可以從 USB 杆進行安裝。  系統會以密碼編譯方式簽署套件，以確保它們源自于所宣告的合作物件。

CNAB 的核心是名為的檔案 `bundle.json` 。 此檔案會定義套件組合的內容，其 Terraform 或影像或其他任何內容。 圖11-9 定義叫用某些 Terraform 的 CNAB。 不過請注意，它實際上會定義用來叫用 Terraform 的叫用映射。 封裝之後，位於 *cnab* 目錄中的 docker 檔案會內建于 docker 映射中，並包含在組合中。 將 Terraform 安裝在套件組合中的 Docker 容器內，表示使用者不需要在其電腦上安裝 Terraform 來執行此套件組合。

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

**圖 10-18** -範例 Terraform 檔

`bundle.json`也會定義一組參數，這些參數會傳遞至 Terraform。 組合的參數化可讓您在各種不同的環境中進行安裝。

CNAB 格式也有彈性，因此可用於任何雲端。 它甚至可以用於內部部署解決方案，例如 [OpenStack](https://www.openstack.org/)。

## <a name="devops-decisions"></a>DevOps 決策

在 DevOps 的空間中，有許多絕佳的工具可讓您在這幾天內順利完成。 DevOps 旅程入門的最愛書籍是 [Phoenix 專案](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)，它會遵循將虛構公司從 NoOps 轉換為 DevOps 的專案。 其中一件事是針對特定的：部署複雜的雲端原生應用程式時，DevOps 不再是「好的」。 這是一項需求，而且應該在任何專案開始時規劃和資源。

## <a name="references"></a>參考資料

- [Azure DevOps](https://azure.microsoft.com/services/devops/)
- [Azure Resource Manager](/azure/azure-resource-manager/management/overview)
- [Terraform](https://www.terraform.io/)
- [Azure CLI](/cli/azure/)

>[!div class="step-by-step"]
>[上一個](infrastructure-as-code.md) 
>[下一步](summary.md)
