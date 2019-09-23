---
title: 基礎結構即程式碼
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |基礎結構即程式碼
ms.date: 06/30/2019
ms.openlocfilehash: e395db28bdeff785251b91ed643f9920873d26e8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183011"
---
# <a name="infrastructure-as-code"></a>基礎結構即程式碼

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雲端原生應用程式通常會使用各種絕佳的平臺即服務（PaaS）元件。 在類似 Azure 的雲端平臺上，這些元件可能包括儲存體、服務匯流排和 SignalR 服務等專案。 隨著應用程式變得更複雜，使用中的服務數目也可能成長。 就像持續傳遞中斷傳統部署至環境的方式一樣，變更的快速步調也會中斷集中式 IT 群組管理環境的模型。

建立環境也可以自動化。 有很廣泛的工具可讓程式變得更容易。

## <a name="azure-resource-manager-templates"></a>Azure Resource Manager 範本

Azure Resource Manager 範本是以 JSON 為基礎的語言，用來定義 Azure 中的各種資源。 基本架構看起來像圖11-10。

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

**圖 11-10** -Resource Manager 範本的架構

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

**圖 11-11** -Resource Manager 範本中定義的儲存體帳戶範例

範本可以參數化，讓一個範本可重複使用不同的設定，以定義開發、QA 和生產環境。 這有助於避免意外遷移至與較低環境設定不同的環境。 範本中定義的資源通常都是在 Azure 上的單一資源群組中建立的（您可以在單一 Resource Manager 範本中定義多個資源群組，但不尋常）。 如此一來，只要刪除整體的資源群組，就可以輕鬆刪除環境。 成本分析也可以在資源群組層級執行，讓您快速地會計每個環境的成本。

GitHub 上的[Azure 快速入門範本](https://github.com/Azure/azure-quickstart-templates)專案中定義了許多範例範本，可在新範本開始時，或將其新增至現有範本時，提供一段時間。

Resource Manager 範本可以多種方式執行。 最簡單的方式是直接將它們貼入 Azure 入口網站。 針對實驗性部署，這個方法可能非常快速。 您也可以在 Azure DevOps 中，以組建或發行進程的一部分來執行它們。 有一些工作會利用 Azure 連線來執行範本。 Resource Manager 範本的變更會以累加方式套用，這表示若要加入新的資源，只需要將它新增至範本。 此工具會處理目前的資源群組與範本中所定義的所需資源群組的比較。 然後會建立或更改資源，使其符合範本中定義的資源。  

## <a name="terraform"></a>Terraform

Resource Manager 範本的認知缺點是它們是 Azure 雲端特有的。 建立包含來自多個雲端資源的應用程式是不尋常的，但如果企業依賴可操作的執行時間，則支援多個雲端的成本可能很值得。 如果有一個可在每個雲端使用的範本化語言，它也可讓開發人員技能更具可攜性。

有幾種技術可以做到！ 該空間中最成熟的供應專案稱為[Terraform](https://www.terraform.io/)。 Terraform 支援每個主要雲端播放機，例如 Azure、Google Cloud Platform、AWS 和 AliCloud，而且也支援數十個次要播放機，例如 Heroku 和 DigitalOcean。 它不使用 JSON 做為範本定義語言，而是使用稍微簡易的 YAML。 

與先前 Resource Manager 範本相同的範例 Terraform 檔（圖11-11）如 [圖 11-12] 所示：

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

**圖 11-12** -Resource Manager 範本的範例

當因為範本發生錯誤而無法部署資源時，Terraform 會更好地提供合理的錯誤訊息。 這是 Resource Manager 範本有一些持續挑戰的領域。 此外，也有一個非常方便的驗證工作，可在組建階段中用來及早捕捉範本錯誤。

如同 Resource Manager 範本，有一些命令列工具可用來部署 Terraform 範本。 Azure Pipelines 中也有可驗證及套用 Terraform 範本的社區建立工作。

如果 Terraform 或 Resource Manager 範本將有趣的值（例如連接字串）輸出到新建立的資料庫，則可以在組建管線中捕捉並用於後續工作。

>[!div class="step-by-step"]
>[上一頁](devops.md)
>[下一頁](application-bundles.md)
