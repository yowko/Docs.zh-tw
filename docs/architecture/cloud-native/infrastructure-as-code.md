---
title: 基礎結構即程式碼
description: 以雲端原生應用程式採用基礎結構即程式碼（IaC）
ms.date: 05/12/2020
ms.openlocfilehash: 309dd8610ab3b72a6c6da5297f109f822520c5ff
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395352"
---
# <a name="infrastructure-as-code"></a>基礎結構即程式碼

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雲端原生系統採用微服務、容器和現代化系統設計，以達成速度和靈活性。 它們提供自動化的組建和發行階段，以確保程式碼的一致和品質。 不過，這只是故事的一部分。 您要如何布建這些系統執行所在的雲端環境？

新式雲端原生應用程式採用廣泛接受的[基礎結構即程式碼](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)做法，或 `IaC` 。  透過 IaC，您可以將平臺布建自動化。 您基本上會將軟體工程實務（例如測試和版本控制）套用至您的 DevOps 實務。 您的基礎結構和部署會自動化、一致且可重複。 就像持續傳遞自動化傳統的手動部署模型一樣，基礎結構即程式碼（IaC）會演變應用程式環境的管理方式。

Azure Resource Manager （ARM）、Terraform 和 Azure 命令列介面（CLI）之類的工具，可讓您以宣告方式編寫腳本所需的雲端基礎結構。

## <a name="azure-resource-manager-templates"></a>Azure 資源管理員範本

ARM 代表[Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/)。 它是內建在 Azure 中並公開為 API 服務的 API 布建引擎。 ARM 可讓您以單一、協調的作業來部署、更新、刪除和管理 Azure 資源群組中包含的資源。 您可以使用以 JSON 為基礎的範本來提供引擎，以指定所需的資源及其設定。 ARM 會自動以正確的順序來協調部署，遵循相依性。 引擎會確保等冪性。 如果所需的資源已存在，且具有相同的設定，則會忽略布建。

Azure Resource Manager 範本是以 JSON 為基礎的語言，用來定義 Azure 中的各種資源。 基本架構看起來像圖10-14。

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

在此範本中，您可能會在 resources 區段內定義儲存體容器，如下所示：

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

ARM 範本可以使用動態環境和設定資訊進行參數化。 這麼做可讓它重複使用，以定義不同的環境，例如開發、QA 或生產環境。 一般來說，此範本會在單一 Azure 資源群組中建立所有資源。 如有需要，您可以在單一 Resource Manager 範本中定義多個資源群組。 藉由刪除資源群組本身，您可以刪除環境中的所有資源。 成本分析也可以在資源群組層級執行，讓您快速地會計每個環境的成本。

GitHub 上的[Azure 快速入門範本](https://github.com/Azure/azure-quickstart-templates)專案中提供許多範例或 ARM 範本。 他們可以協助加速建立新範本或修改現有範本。

Resource Manager 範本可以透過許多方式執行。 最簡單的方式是直接將它們貼入 Azure 入口網站。 針對實驗性部署，這個方法可以快速地進行。 您也可以在 Azure DevOps 中，以組建或發行進程的一部分來執行它們。 有一些工作會利用 Azure 連線來執行範本。 Resource Manager 範本的變更會以累加方式套用，這表示若要加入新的資源，只需要將它新增至範本。 此工具會協調目前資源與範本中所定義的差異。 然後會建立或更改資源，使其符合範本中定義的資源。  

## <a name="terraform"></a>Terraform

雲端原生應用程式通常會結構化為 `cloud agnostic` 。 因此，應用程式不會與特定雲端廠商緊密結合，而且可以部署到任何公用雲端。

[Terraform](https://www.terraform.io/)是商業樣板化工具，可在所有主要雲端播放機上布建雲端原生應用程式： Azure、GOOGLE CLOUD PLATFORM、AWS 和 AliCloud。 它不使用 JSON 做為範本定義語言，而是使用稍微簡易的 YAML。

與先前 Resource Manager 範本相同的範例 Terraform 檔（圖10-15）如 [圖 10-16] 所示：

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

Terraform 也會為問題範本提供直覺錯誤訊息。 此外，也有一個方便的驗證工作，可在組建階段中用來及早捕捉範本錯誤。

如同 Resource Manager 範本，可以使用命令列工具來部署 Terraform 範本。 Azure Pipelines 中也有可驗證及套用 Terraform 範本的社區建立工作。

有時候，Terraform 和 ARM 範本會輸出有意義的值，例如新建立之資料庫的連接字串。 這項資訊可在組建管線中捕捉，並用於後續工作。

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLI 腳本和工作

最後，您可以利用[Azure CLI](https://docs.microsoft.com/cli/azure/)以宣告方式編寫您的雲端基礎結構腳本。 您可以建立、尋找和共用 Azure CLI 腳本，以布建及設定幾乎所有的 Azure 資源。 CLI 很容易與簡單的學習曲線搭配使用。 腳本會在 PowerShell 或 Bash 中執行。 它們也很容易進行調試，特別是與 ARM 範本比較時。

當您需要卸載並重新部署您的基礎結構時，Azure CLI 腳本會運作良好。 更新現有的環境可能會很棘手。 許多 CLI 命令不具等冪性。 這表示它們會在每次執行時重新建立資源，即使資源已經存在也一樣。 在建立程式碼之前，一律可以加入檢查每個資源是否存在的程式碼。 但是，您的腳本可能會變得膨脹，而且很難以管理。

這些腳本也可以內嵌在 Azure DevOps 管線中，做為 `Azure CLI tasks` 。 執行管線會叫用腳本。

圖10-17 顯示 YAML 程式碼片段，其中列出 Azure CLI 的版本和訂用帳戶的詳細資料。 請注意，內嵌腳本中包含 Azure CLI 命令的方式。

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

在本文中，[什麼是基礎結構即程式碼](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)，作者 Sam 作者: guckenheimer 說明如何，「執行 IaC 的小組可以快速且大規模地提供穩定的環境。 小組會避免手動設定環境，並藉由透過程式碼來表示其環境的期望狀態來強制執行一致性。 使用 IaC 的基礎結構部署可重複，並防止設定漂移或遺失相依性所造成的執行時間問題。 DevOps 小組可以與一組整合的實務和工具搭配運作，以快速、可靠且大規模地傳遞應用程式及其支援的基礎結構。」

>[!div class="step-by-step"]
>[上一個](feature-flags.md) 
>[下一步](application-bundles.md)
