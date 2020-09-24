---
title: 基礎結構即程式碼
description: '使用雲端原生應用程式將基礎結構作為程式碼 (IaC) '
ms.date: 05/13/2020
ms.openlocfilehash: d130705e19e0d3d7a9e15c73f4758a22ee8ecd43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163735"
---
# <a name="infrastructure-as-code"></a>基礎結構即程式碼

雲端原生系統採用微服務、容器和新式系統設計，以達成速度和靈活性。 它們提供自動化的組建和發行階段，以確保一致且品質的程式碼。 但是，這只是故事的一部分。 如何布建這些系統執行所在的雲端環境？

新式雲端原生應用程式採用廣泛接受的 [基礎結構即程式碼](/azure/devops/learn/what-is-infrastructure-as-code)做法，或 `IaC` 。  透過 IaC，您可以將平臺布建自動化。 您基本上會將軟體工程實務（例如測試和版本控制）套用至您的 DevOps 實務。 您的基礎結構和部署是自動化、一致且可重複的。 如同持續傳遞，將傳統的手動部署模型自動化，基礎結構即程式碼 (IaC) 正在發展應用程式環境的管理方式。

Azure Resource Manager (ARM) 、Terraform 和 Azure 命令列介面等工具 (CLI) 可讓您以宣告方式編寫所需的雲端基礎結構腳本。

## <a name="azure-resource-manager-templates"></a>Azure 資源管理員範本

ARM 代表 [Azure Resource Manager](/azure/azure-resource-manager/management/overview)。 它是內建于 Azure 並公開為 API 服務的 API 布建引擎。 ARM 可讓您以單一、協調的作業來部署、更新、刪除及管理 Azure 資源群組中包含的資源。 您可以為引擎提供以 JSON 為基礎的範本，以指定您需要的資源及其設定。 ARM 會自動以遵循相依性的正確順序來協調部署。 引擎可確保等冪性。 如果所需的資源已經有相同的設定，將會忽略布建。

Azure Resource Manager 範本是以 JSON 為基礎的語言，可用於定義 Azure 中的各種資源。 基本架構看起來像圖10-14。

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

**圖 10-14** -Resource Manager 範本的架構

在此範本中，您可能會在資源區段內定義儲存體容器，如下所示：

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

**圖 10-15** -Resource Manager 範本中定義的儲存體帳戶範例

您可以使用動態環境和設定資訊，將 ARM 範本參數化。 這麼做可讓它重複使用，以定義不同的環境，例如開發、QA 或生產環境。 一般來說，此範本會在單一 Azure 資源群組中建立所有資源。 您可以視需要在單一 Resource Manager 範本中定義多個資源群組。 您可以藉由刪除資源群組本身來刪除環境中的所有資源。 成本分析也可以在資源群組層級執行，讓您可以快速地計算每個環境的計費方式。

GitHub 上的 [Azure 快速入門範本](https://github.com/Azure/azure-quickstart-templates) 專案中有許多範例或 ARM 範本可供使用。 它們可協助加速建立新範本或修改現有範本。

您可以透過許多方式來執行 Resource Manager 範本。 或許最簡單的方式是將它們貼入 Azure 入口網站中。 針對實驗性部署，這種方法可以快速進行。 它們也可以在 Azure DevOps 的組建或發行流程中執行。 有一些工作會利用連接至 Azure 來執行範本。 Resource Manager 範本的變更會以累加方式套用，這表示若要加入新的資源，則只需要將它新增至範本。 這些工具會協調目前資源與範本中定義的差異。 接著會建立或變更資源，使其符合範本中定義的資源。  

## <a name="terraform"></a>Terraform

雲端原生應用程式通常會視為 `cloud agnostic` 。 如此一來，應用程式就不會與特定的雲端廠商緊密結合，而且可以部署到任何公用雲端。

[Terraform](https://www.terraform.io/) 是商業範本化工具，可在所有主要雲端播放機上布建雲端原生應用程式： Azure、GOOGLE CLOUD PLATFORM、AWS 和 AliCloud。 它不會使用 JSON 作為範本定義語言，而是使用稍微簡易的 YAML。

與先前的 Resource Manager 範本相同的範例 Terraform 檔 (圖 10-15) 如圖10-16 所示：

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

**圖 10-16** -Resource Manager 範本的範例

Terraform 也提供問題範本的直覺錯誤訊息。 另外還有一個方便的驗證工作，可在組建階段用來及早攔截範本錯誤。

如同 Resource Manager 範本，您可以使用命令列工具來部署 Terraform 範本。 在 Azure Pipelines 中也有可驗證及套用 Terraform 範本的社區建立工作。

有時 Terraform 和 ARM 範本會輸出有意義的值，例如新建立之資料庫的連接字串。 這項資訊可以在組建管線中捕捉，並用於後續的工作。

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLI 腳本和工作

最後，您可以利用 [Azure CLI](/cli/azure/) 以宣告方式編寫雲端基礎結構的腳本。 您可以建立、尋找和共用 Azure CLI 腳本，以布建及設定幾乎任何 Azure 資源。 CLI 很容易與平滑學習曲線一起使用。 腳本會在 PowerShell 或 Bash 中執行。 它們也可以直接進行調試，尤其是與 ARM 範本比較時。

當您需要卸載和重新部署基礎結構時，Azure CLI 腳本的運作效果很好。 更新現有的環境可能有點棘手。 許多 CLI 命令都不具等冪性。 這表示它們會在每次執行時重新建立資源，即使資源已存在也一樣。 您一律可以新增程式碼，以在建立每個資源之前先檢查是否存在。 但是這麼做，您的腳本可能會變得膨脹且難以管理。

這些腳本也可以內嵌在 Azure DevOps 管線中 `Azure CLI tasks` 。 執行管線會叫用腳本。

圖10-17 顯示的 YAML 程式碼片段會列出 Azure CLI 的版本以及訂用帳戶的詳細資料。 請注意內嵌腳本中包含 Azure CLI 命令的方式。

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

**圖 10-17** -Azure CLI 腳本

在這篇文章中， [什麼是基礎結構即程式碼](/azure/devops/learn/what-is-infrastructure-as-code)，作者 Sam 作者: guckenheimer 描述了「如何」，這是「實行 IaC 的團隊可以快速且大規模地提供穩定的環境。 小組避免手動設定環境，並透過程式碼代表其環境的預期狀態，來強制執行一致性。 使用 IaC 的基礎結構部署是可重複的，可防止設定漂移或遺失相依性所造成的執行時間問題。 DevOps 團隊可以搭配一組整合的實務和工具，快速、可靠且大規模地傳遞應用程式及其支援的基礎結構。」

>[!div class="step-by-step"]
>[上一個](feature-flags.md) 
>[下一步](application-bundles.md)
