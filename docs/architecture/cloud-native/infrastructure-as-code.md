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
# <a name="infrastructure-as-code"></a><span data-ttu-id="3f811-103">基礎結構即程式碼</span><span class="sxs-lookup"><span data-stu-id="3f811-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3f811-104">雲端原生應用程式通常會使用各種絕佳的平臺即服務（PaaS）元件。</span><span class="sxs-lookup"><span data-stu-id="3f811-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="3f811-105">在類似 Azure 的雲端平臺上，這些元件可能包括儲存體、服務匯流排和 SignalR 服務等專案。</span><span class="sxs-lookup"><span data-stu-id="3f811-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="3f811-106">隨著應用程式變得更複雜，使用中的服務數目也可能成長。</span><span class="sxs-lookup"><span data-stu-id="3f811-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="3f811-107">就像持續傳遞中斷傳統部署至環境的方式一樣，變更的快速步調也會中斷集中式 IT 群組管理環境的模型。</span><span class="sxs-lookup"><span data-stu-id="3f811-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="3f811-108">建立環境也可以自動化。</span><span class="sxs-lookup"><span data-stu-id="3f811-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="3f811-109">有很廣泛的工具可讓程式變得更容易。</span><span class="sxs-lookup"><span data-stu-id="3f811-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="3f811-110">Azure Resource Manager 範本</span><span class="sxs-lookup"><span data-stu-id="3f811-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="3f811-111">Azure Resource Manager 範本是以 JSON 為基礎的語言，用來定義 Azure 中的各種資源。</span><span class="sxs-lookup"><span data-stu-id="3f811-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="3f811-112">基本架構看起來像圖11-10。</span><span class="sxs-lookup"><span data-stu-id="3f811-112">The basic schema looks something like Figure 11-10.</span></span>

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

<span data-ttu-id="3f811-113">**圖 11-10** -Resource Manager 範本的架構</span><span class="sxs-lookup"><span data-stu-id="3f811-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="3f811-114">在此範本中，您可能會在 resources 區段內定義儲存體容器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f811-114">Within this template, one might define a storage container inside the resources section like so:</span></span>
 
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

<span data-ttu-id="3f811-115">**圖 11-11** -Resource Manager 範本中定義的儲存體帳戶範例</span><span class="sxs-lookup"><span data-stu-id="3f811-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="3f811-116">範本可以參數化，讓一個範本可重複使用不同的設定，以定義開發、QA 和生產環境。</span><span class="sxs-lookup"><span data-stu-id="3f811-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="3f811-117">這有助於避免意外遷移至與較低環境設定不同的環境。</span><span class="sxs-lookup"><span data-stu-id="3f811-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="3f811-118">範本中定義的資源通常都是在 Azure 上的單一資源群組中建立的（您可以在單一 Resource Manager 範本中定義多個資源群組，但不尋常）。</span><span class="sxs-lookup"><span data-stu-id="3f811-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="3f811-119">如此一來，只要刪除整體的資源群組，就可以輕鬆刪除環境。</span><span class="sxs-lookup"><span data-stu-id="3f811-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="3f811-120">成本分析也可以在資源群組層級執行，讓您快速地會計每個環境的成本。</span><span class="sxs-lookup"><span data-stu-id="3f811-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="3f811-121">GitHub 上的[Azure 快速入門範本](https://github.com/Azure/azure-quickstart-templates)專案中定義了許多範例範本，可在新範本開始時，或將其新增至現有範本時，提供一段時間。</span><span class="sxs-lookup"><span data-stu-id="3f811-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="3f811-122">Resource Manager 範本可以多種方式執行。</span><span class="sxs-lookup"><span data-stu-id="3f811-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="3f811-123">最簡單的方式是直接將它們貼入 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="3f811-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="3f811-124">針對實驗性部署，這個方法可能非常快速。</span><span class="sxs-lookup"><span data-stu-id="3f811-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="3f811-125">您也可以在 Azure DevOps 中，以組建或發行進程的一部分來執行它們。</span><span class="sxs-lookup"><span data-stu-id="3f811-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="3f811-126">有一些工作會利用 Azure 連線來執行範本。</span><span class="sxs-lookup"><span data-stu-id="3f811-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="3f811-127">Resource Manager 範本的變更會以累加方式套用，這表示若要加入新的資源，只需要將它新增至範本。</span><span class="sxs-lookup"><span data-stu-id="3f811-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="3f811-128">此工具會處理目前的資源群組與範本中所定義的所需資源群組的比較。</span><span class="sxs-lookup"><span data-stu-id="3f811-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="3f811-129">然後會建立或更改資源，使其符合範本中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="3f811-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="3f811-130">Terraform</span><span class="sxs-lookup"><span data-stu-id="3f811-130">Terraform</span></span>

<span data-ttu-id="3f811-131">Resource Manager 範本的認知缺點是它們是 Azure 雲端特有的。</span><span class="sxs-lookup"><span data-stu-id="3f811-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="3f811-132">建立包含來自多個雲端資源的應用程式是不尋常的，但如果企業依賴可操作的執行時間，則支援多個雲端的成本可能很值得。</span><span class="sxs-lookup"><span data-stu-id="3f811-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="3f811-133">如果有一個可在每個雲端使用的範本化語言，它也可讓開發人員技能更具可攜性。</span><span class="sxs-lookup"><span data-stu-id="3f811-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="3f811-134">有幾種技術可以做到！</span><span class="sxs-lookup"><span data-stu-id="3f811-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="3f811-135">該空間中最成熟的供應專案稱為[Terraform](https://www.terraform.io/)。</span><span class="sxs-lookup"><span data-stu-id="3f811-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="3f811-136">Terraform 支援每個主要雲端播放機，例如 Azure、Google Cloud Platform、AWS 和 AliCloud，而且也支援數十個次要播放機，例如 Heroku 和 DigitalOcean。</span><span class="sxs-lookup"><span data-stu-id="3f811-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="3f811-137">它不使用 JSON 做為範本定義語言，而是使用稍微簡易的 YAML。</span><span class="sxs-lookup"><span data-stu-id="3f811-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span> 

<span data-ttu-id="3f811-138">與先前 Resource Manager 範本相同的範例 Terraform 檔（圖11-11）如 [圖 11-12] 所示：</span><span class="sxs-lookup"><span data-stu-id="3f811-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

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

<span data-ttu-id="3f811-139">**圖 11-12** -Resource Manager 範本的範例</span><span class="sxs-lookup"><span data-stu-id="3f811-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="3f811-140">當因為範本發生錯誤而無法部署資源時，Terraform 會更好地提供合理的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3f811-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="3f811-141">這是 Resource Manager 範本有一些持續挑戰的領域。</span><span class="sxs-lookup"><span data-stu-id="3f811-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="3f811-142">此外，也有一個非常方便的驗證工作，可在組建階段中用來及早捕捉範本錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f811-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="3f811-143">如同 Resource Manager 範本，有一些命令列工具可用來部署 Terraform 範本。</span><span class="sxs-lookup"><span data-stu-id="3f811-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="3f811-144">Azure Pipelines 中也有可驗證及套用 Terraform 範本的社區建立工作。</span><span class="sxs-lookup"><span data-stu-id="3f811-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="3f811-145">如果 Terraform 或 Resource Manager 範本將有趣的值（例如連接字串）輸出到新建立的資料庫，則可以在組建管線中捕捉並用於後續工作。</span><span class="sxs-lookup"><span data-stu-id="3f811-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3f811-146">[上一頁](devops.md)
>[下一頁](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="3f811-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
