---
title: 雲端原生應用程式套件組合
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式套件組合
ms.date: 06/30/2019
ms.openlocfilehash: 0c67035af08d3c337ff027f3742e1ce8a83f8d0f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183711"
---
# <a name="cloud-native-application-bundles"></a>雲端原生應用程式套件組合

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雲端原生應用程式的重要屬性是，它們會利用雲端的屬性來加速開發。 這通常表示完整的應用程式會使用不同種類的技術。 應用程式可能會隨附在 Docker 容器中，有些服務可能會使用 Azure Functions 而其他部分則可直接在使用硬體 GPU 加速在大型金屬伺服器上配置的虛擬機器上執行。 沒有兩個雲端原生應用程式相同，因此很難以提供傳送它們的單一機制。

Docker 容器可在 Kubernetes 上執行，並使用 Helm 圖表進行部署。 Azure Functions 可以使用 Terraform 範本進行配置。 最後，您可以使用 Terraform 來配置虛擬機器，但使用 Ansible 來建立。 這是一項完整的技術，而且沒有辦法將它們全部封裝在一起，成為合理的套件。 到目前為止。

雲端原生應用程式套件組合（CNABs）是許多意識公司（例如 Microsoft、Docker 和 HashiCorp）的共同工作，可開發用來封裝分散式應用程式的規格。

這項工作是在2018年12月宣佈的，因此，仍然需要執行一項工作，將工作暴露于更大的社區。 不過，已經有[開放式規格](https://github.com/deislabs/cnab-spec)和參考實，稱為[行李](https://duffle.sh/)。 這項工具是以 Go 撰寫，這是 Docker 與 Microsoft 之間的共同投入。

CNABs 可以包含不同種類的安裝技術。 如此一來，Helm 圖、Terraform 範本和 Ansible 的操作手冊就可以並存于相同的套件中。 建立之後，套件是獨立且可移植的;您可以從 USB 卡安裝它們。  系統會以密碼編譯方式簽署套件，以確保它們源自于其宣告的合作物件。

CNAB 的核心是名`bundle.json`為的檔案。 此檔案會定義組合的內容，其 Terraform 或影像，或其他任何專案。 圖11-9 定義了叫用一些 Terraform 的 CNAB。 不過，請注意，它實際上會定義用來叫用 Terraform 的調用影像。 當封裝時，位於*cnab*目錄中的 docker 檔案會內建到 docker 映射中，並包含在組合中。 將 Terraform 安裝在配套中的 Docker 容器內，表示使用者不需要在其電腦上安裝 Terraform 來執行配套。

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

**圖 11-13** -範例 Terraform 檔案

`bundle.json`也會定義一組傳遞至 Terraform 的參數。 組合的參數化可讓您在各種不同的環境中安裝。

CNAB 格式也有彈性，讓它可用於任何雲端。 它甚至可以用於內部部署解決方案，例如[OpenStack](https://www.openstack.org/)。

## <a name="devops-decisions"></a>DevOps 決策

在 DevOps 的空間中，有很多絕佳的工具可讓您順利完成。 開始使用 DevOps 旅程的最愛書是[Phoenix 專案](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)，其遵循將虛構公司從 NoOps 轉換為 DevOps。 其中一件事是：部署複雜的雲端原生應用程式時，DevOps 不再是「不錯的」。 這是一項需求，而且應該在任何專案開始時規劃和資源。

>[!div class="step-by-step"]
>[上一步](infrastructure-as-code.md)
