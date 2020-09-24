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
# <a name="infrastructure-as-code"></a><span data-ttu-id="bbc0d-103">基礎結構即程式碼</span><span class="sxs-lookup"><span data-stu-id="bbc0d-103">Infrastructure as code</span></span>

<span data-ttu-id="bbc0d-104">雲端原生系統採用微服務、容器和新式系統設計，以達成速度和靈活性。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="bbc0d-105">它們提供自動化的組建和發行階段，以確保一致且品質的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="bbc0d-106">但是，這只是故事的一部分。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-106">But, that's only part of the story.</span></span> <span data-ttu-id="bbc0d-107">如何布建這些系統執行所在的雲端環境？</span><span class="sxs-lookup"><span data-stu-id="bbc0d-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="bbc0d-108">新式雲端原生應用程式採用廣泛接受的 [基礎結構即程式碼](/azure/devops/learn/what-is-infrastructure-as-code)做法，或 `IaC` 。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="bbc0d-109">透過 IaC，您可以將平臺布建自動化。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="bbc0d-110">您基本上會將軟體工程實務（例如測試和版本控制）套用至您的 DevOps 實務。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="bbc0d-111">您的基礎結構和部署是自動化、一致且可重複的。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="bbc0d-112">如同持續傳遞，將傳統的手動部署模型自動化，基礎結構即程式碼 (IaC) 正在發展應用程式環境的管理方式。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="bbc0d-113">Azure Resource Manager (ARM) 、Terraform 和 Azure 命令列介面等工具 (CLI) 可讓您以宣告方式編寫所需的雲端基礎結構腳本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="bbc0d-114">Azure 資源管理員範本</span><span class="sxs-lookup"><span data-stu-id="bbc0d-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="bbc0d-115">ARM 代表 [Azure Resource Manager](/azure/azure-resource-manager/management/overview)。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-115">ARM stands for [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span></span> <span data-ttu-id="bbc0d-116">它是內建于 Azure 並公開為 API 服務的 API 布建引擎。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="bbc0d-117">ARM 可讓您以單一、協調的作業來部署、更新、刪除及管理 Azure 資源群組中包含的資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="bbc0d-118">您可以為引擎提供以 JSON 為基礎的範本，以指定您需要的資源及其設定。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="bbc0d-119">ARM 會自動以遵循相依性的正確順序來協調部署。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="bbc0d-120">引擎可確保等冪性。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-120">The engine ensures idempotency.</span></span> <span data-ttu-id="bbc0d-121">如果所需的資源已經有相同的設定，將會忽略布建。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="bbc0d-122">Azure Resource Manager 範本是以 JSON 為基礎的語言，可用於定義 Azure 中的各種資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="bbc0d-123">基本架構看起來像圖10-14。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="bbc0d-124">**圖 10-14** -Resource Manager 範本的架構</span><span class="sxs-lookup"><span data-stu-id="bbc0d-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="bbc0d-125">在此範本中，您可能會在資源區段內定義儲存體容器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bbc0d-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="bbc0d-126">**圖 10-15** -Resource Manager 範本中定義的儲存體帳戶範例</span><span class="sxs-lookup"><span data-stu-id="bbc0d-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="bbc0d-127">您可以使用動態環境和設定資訊，將 ARM 範本參數化。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="bbc0d-128">這麼做可讓它重複使用，以定義不同的環境，例如開發、QA 或生產環境。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="bbc0d-129">一般來說，此範本會在單一 Azure 資源群組中建立所有資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="bbc0d-130">您可以視需要在單一 Resource Manager 範本中定義多個資源群組。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="bbc0d-131">您可以藉由刪除資源群組本身來刪除環境中的所有資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="bbc0d-132">成本分析也可以在資源群組層級執行，讓您可以快速地計算每個環境的計費方式。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="bbc0d-133">GitHub 上的 [Azure 快速入門範本](https://github.com/Azure/azure-quickstart-templates) 專案中有許多範例或 ARM 範本可供使用。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="bbc0d-134">它們可協助加速建立新範本或修改現有範本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="bbc0d-135">您可以透過許多方式來執行 Resource Manager 範本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="bbc0d-136">或許最簡單的方式是將它們貼入 Azure 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="bbc0d-137">針對實驗性部署，這種方法可以快速進行。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="bbc0d-138">它們也可以在 Azure DevOps 的組建或發行流程中執行。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="bbc0d-139">有一些工作會利用連接至 Azure 來執行範本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="bbc0d-140">Resource Manager 範本的變更會以累加方式套用，這表示若要加入新的資源，則只需要將它新增至範本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="bbc0d-141">這些工具會協調目前資源與範本中定義的差異。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="bbc0d-142">接著會建立或變更資源，使其符合範本中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="bbc0d-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="bbc0d-143">Terraform</span></span>

<span data-ttu-id="bbc0d-144">雲端原生應用程式通常會視為 `cloud agnostic` 。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="bbc0d-145">如此一來，應用程式就不會與特定的雲端廠商緊密結合，而且可以部署到任何公用雲端。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="bbc0d-146">[Terraform](https://www.terraform.io/) 是商業範本化工具，可在所有主要雲端播放機上布建雲端原生應用程式： Azure、GOOGLE CLOUD PLATFORM、AWS 和 AliCloud。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="bbc0d-147">它不會使用 JSON 作為範本定義語言，而是使用稍微簡易的 YAML。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="bbc0d-148">與先前的 Resource Manager 範本相同的範例 Terraform 檔 (圖 10-15) 如圖10-16 所示：</span><span class="sxs-lookup"><span data-stu-id="bbc0d-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="bbc0d-149">**圖 10-16** -Resource Manager 範本的範例</span><span class="sxs-lookup"><span data-stu-id="bbc0d-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="bbc0d-150">Terraform 也提供問題範本的直覺錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="bbc0d-151">另外還有一個方便的驗證工作，可在組建階段用來及早攔截範本錯誤。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="bbc0d-152">如同 Resource Manager 範本，您可以使用命令列工具來部署 Terraform 範本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="bbc0d-153">在 Azure Pipelines 中也有可驗證及套用 Terraform 範本的社區建立工作。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="bbc0d-154">有時 Terraform 和 ARM 範本會輸出有意義的值，例如新建立之資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="bbc0d-155">這項資訊可以在組建管線中捕捉，並用於後續的工作。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="bbc0d-156">Azure CLI 腳本和工作</span><span class="sxs-lookup"><span data-stu-id="bbc0d-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="bbc0d-157">最後，您可以利用 [Azure CLI](/cli/azure/) 以宣告方式編寫雲端基礎結構的腳本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-157">Finally, you can leverage [Azure CLI](/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="bbc0d-158">您可以建立、尋找和共用 Azure CLI 腳本，以布建及設定幾乎任何 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="bbc0d-159">CLI 很容易與平滑學習曲線一起使用。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="bbc0d-160">腳本會在 PowerShell 或 Bash 中執行。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="bbc0d-161">它們也可以直接進行調試，尤其是與 ARM 範本比較時。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="bbc0d-162">當您需要卸載和重新部署基礎結構時，Azure CLI 腳本的運作效果很好。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="bbc0d-163">更新現有的環境可能有點棘手。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="bbc0d-164">許多 CLI 命令都不具等冪性。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="bbc0d-165">這表示它們會在每次執行時重新建立資源，即使資源已存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="bbc0d-166">您一律可以新增程式碼，以在建立每個資源之前先檢查是否存在。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="bbc0d-167">但是這麼做，您的腳本可能會變得膨脹且難以管理。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="bbc0d-168">這些腳本也可以內嵌在 Azure DevOps 管線中 `Azure CLI tasks` 。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="bbc0d-169">執行管線會叫用腳本。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="bbc0d-170">圖10-17 顯示的 YAML 程式碼片段會列出 Azure CLI 的版本以及訂用帳戶的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="bbc0d-171">請注意內嵌腳本中包含 Azure CLI 命令的方式。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-171">Note how Azure CLI commands are included in an inline script.</span></span>

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

<span data-ttu-id="bbc0d-172">**圖 10-17** -Azure CLI 腳本</span><span class="sxs-lookup"><span data-stu-id="bbc0d-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="bbc0d-173">在這篇文章中， [什麼是基礎結構即程式碼](/azure/devops/learn/what-is-infrastructure-as-code)，作者 Sam 作者: guckenheimer 描述了「如何」，這是「實行 IaC 的團隊可以快速且大規模地提供穩定的環境。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-173">In the article, [What is Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="bbc0d-174">小組避免手動設定環境，並透過程式碼代表其環境的預期狀態，來強制執行一致性。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="bbc0d-175">使用 IaC 的基礎結構部署是可重複的，可防止設定漂移或遺失相依性所造成的執行時間問題。</span><span class="sxs-lookup"><span data-stu-id="bbc0d-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="bbc0d-176">DevOps 團隊可以搭配一組整合的實務和工具，快速、可靠且大規模地傳遞應用程式及其支援的基礎結構。」</span><span class="sxs-lookup"><span data-stu-id="bbc0d-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bbc0d-177">[上一個](feature-flags.md) 
>[下一步](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="bbc0d-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
