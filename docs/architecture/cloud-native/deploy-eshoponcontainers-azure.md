---
title: 將 eShopOnContainers 部署至 Azure
description: 使用 Azure Kubernetes Service、Helm 和 DevSpaces 部署 eShopOnContainers 應用程式。
ms.date: 04/20/2020
ms.openlocfilehash: a3eacedac946cb25cf3cced305d7921e29f0d204
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895588"
---
# <a name="deploying-eshoponcontainers-to-azure"></a><span data-ttu-id="acd3f-103">將 eShopOnContainers 部署至 Azure</span><span class="sxs-lookup"><span data-stu-id="acd3f-103">Deploying eShopOnContainers to Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="acd3f-104">EShopOnContainers 應用程式可以部署至各種不同的 Azure 平臺。</span><span class="sxs-lookup"><span data-stu-id="acd3f-104">The eShopOnContainers application can be deployed to a variety of Azure platforms.</span></span> <span data-ttu-id="acd3f-105">建議的方法是將應用程式部署至 Azure Kubernetes Services （AKS）。</span><span class="sxs-lookup"><span data-stu-id="acd3f-105">The recommended approach is to deploy the application to Azure Kubernetes Services (AKS).</span></span> <span data-ttu-id="acd3f-106">Helm 是一種 Kubernetes 的部署工具，可用來降低部署複雜度。</span><span class="sxs-lookup"><span data-stu-id="acd3f-106">Helm, a Kubernetes deployment tool, is available to reduce deployment complexity.</span></span> <span data-ttu-id="acd3f-107">開發人員可以選擇性地執行 Azure Dev Spaces Kubernetes，以簡化其開發流程。</span><span class="sxs-lookup"><span data-stu-id="acd3f-107">Optionally, developers may implement Azure Dev Spaces for Kubernetes to streamline their development process.</span></span>

## <a name="azure-kubernetes-service"></a><span data-ttu-id="acd3f-108">Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="acd3f-108">Azure Kubernetes Service</span></span>

<span data-ttu-id="acd3f-109">若要在 AKS 中裝載 eShop，第一個步驟是建立 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="acd3f-109">To host eShop in AKS, the first step is to create an AKS cluster.</span></span> <span data-ttu-id="acd3f-110">若要這麼做，您可以使用 Azure 入口網站，這會引導您完成必要的步驟。</span><span class="sxs-lookup"><span data-stu-id="acd3f-110">To do so, you might use the Azure portal, which will walk you through the required steps.</span></span> <span data-ttu-id="acd3f-111">您也可以從 Azure CLI 建立叢集，並負責啟用角色型存取控制（RBAC）和應用程式路由。</span><span class="sxs-lookup"><span data-stu-id="acd3f-111">You could also create a cluster from the Azure CLI, taking care to enable Role-Based Access Control (RBAC) and application routing.</span></span> <span data-ttu-id="acd3f-112">EShopOnContainers 的檔詳細說明建立您自己的 AKS 叢集的步驟。</span><span class="sxs-lookup"><span data-stu-id="acd3f-112">The eShopOnContainers' documentation details the steps for creating your own AKS cluster.</span></span> <span data-ttu-id="acd3f-113">建立之後，您就可以從 Kubernetes 儀表板存取和管理叢集。</span><span class="sxs-lookup"><span data-stu-id="acd3f-113">Once created, you can access and manage the cluster from the Kubernetes dashboard.</span></span>

<span data-ttu-id="acd3f-114">您現在可以利用 Helm 和 Tiller，將 eShop 應用程式部署到叢集。</span><span class="sxs-lookup"><span data-stu-id="acd3f-114">You can now deploy the eShop application to the cluster leveraging Helm and Tiller.</span></span>

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a><span data-ttu-id="acd3f-115">使用 Helm 部署到 Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="acd3f-115">Deploying to Azure Kubernetes Service using Helm</span></span>

<span data-ttu-id="acd3f-116">Helm 是直接與 Kubernetes 搭配運作的應用程式套件管理員工具。</span><span class="sxs-lookup"><span data-stu-id="acd3f-116">Helm is an application package manager tool that works directly with Kubernetes.</span></span> <span data-ttu-id="acd3f-117">它可協助您定義、安裝及升級 Kubernetes 應用程式。</span><span class="sxs-lookup"><span data-stu-id="acd3f-117">It helps you define, install, and upgrade Kubernetes applications.</span></span> <span data-ttu-id="acd3f-118">雖然可以使用自訂的 CLI 腳本或簡單的部署檔案來部署簡單的應用程式 AKS，但複雜的應用程式可以包含許多 Kubernetes 物件，並受益于 Helm。</span><span class="sxs-lookup"><span data-stu-id="acd3f-118">While simple apps can be deployed to AKS with custom CLI scripts or simple deployment files, complex apps can contain many Kubernetes objects and benefit from Helm.</span></span>

<span data-ttu-id="acd3f-119">應用程式會使用 Helm，包括以文字為基礎的設定檔，稱為 Helm 圖表，以宣告方式描述 Helm 套件中的應用程式和設定。</span><span class="sxs-lookup"><span data-stu-id="acd3f-119">Using Helm, applications include text-based configuration files, called Helm charts, which declaratively describe the application and configuration in Helm packages.</span></span> <span data-ttu-id="acd3f-120">圖表使用標準 YAML 格式的檔案來描述一組相關的 Kubernetes 資源。</span><span class="sxs-lookup"><span data-stu-id="acd3f-120">Charts use standard YAML-formatted files to describe a related set of Kubernetes resources.</span></span> <span data-ttu-id="acd3f-121">它們會與它們所描述的應用程式代碼一起建立版本。</span><span class="sxs-lookup"><span data-stu-id="acd3f-121">They're versioned alongside the application code they describe.</span></span> <span data-ttu-id="acd3f-122">Helm 圖表的範圍從簡單到複雜，視其所描述的安裝需求而定。</span><span class="sxs-lookup"><span data-stu-id="acd3f-122">Helm Charts range from simple to complex depending on the requirements of the installation they describe.</span></span>

<span data-ttu-id="acd3f-123">Helm 是由命令列用戶端工具所組成，它會取用 Helm 圖表，並對名為 Tiller 的伺服器元件啟動命令。</span><span class="sxs-lookup"><span data-stu-id="acd3f-123">Helm is composed of a command-line client tool, which consumes helm charts and launches commands to a server component named, Tiller.</span></span> <span data-ttu-id="acd3f-124">Tiller 會與 Kubernetes API 通訊，以確保容器化工作負載的正確布建。</span><span class="sxs-lookup"><span data-stu-id="acd3f-124">Tiller communicates with the Kubernetes API to ensure the correct provisioning of your containerized workloads.</span></span> <span data-ttu-id="acd3f-125">Helm 是由雲端原生計算基礎所維護。</span><span class="sxs-lookup"><span data-stu-id="acd3f-125">Helm is maintained by the Cloud-native Computing Foundation.</span></span>

<span data-ttu-id="acd3f-126">下列 yaml 檔提供 Helm 範本：</span><span class="sxs-lookup"><span data-stu-id="acd3f-126">The following yaml file presents a Helm template:</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

<span data-ttu-id="acd3f-127">請注意範本如何描述一組動態的索引鍵/值配對。</span><span class="sxs-lookup"><span data-stu-id="acd3f-127">Note how the template describes a dynamic set of key/value pairs.</span></span> <span data-ttu-id="acd3f-128">叫用範本時，括在大括弧中的值會從其他以 yaml 為基礎的設定檔提取。</span><span class="sxs-lookup"><span data-stu-id="acd3f-128">When the template is invoked, values that enclosed in curly braces are pulled in from other yaml-based configuration files.</span></span>

<span data-ttu-id="acd3f-129">您會在/k8s/helm 資料夾中找到 eShopOnContainers helm 圖表。</span><span class="sxs-lookup"><span data-stu-id="acd3f-129">You'll find the eShopOnContainers helm charts in the /k8s/helm folder.</span></span> <span data-ttu-id="acd3f-130">圖2-6 顯示如何將應用程式的不同元件組織成 helm 用來定義和管理部署的資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="acd3f-130">Figure 2-6 shows how the different components of the application are organized into a folder structure used by helm to define and managed deployments.</span></span>

<span data-ttu-id="acd3f-131">![eShopOnContainers 架構](./media/eshoponcontainers-helm-folder.png)
**圖 2-6**。</span><span class="sxs-lookup"><span data-stu-id="acd3f-131">![eShopOnContainers Architecture](./media/eshoponcontainers-helm-folder.png)
**Figure 2-6**.</span></span> <span data-ttu-id="acd3f-132">EShopOnContainers helm 資料夾。</span><span class="sxs-lookup"><span data-stu-id="acd3f-132">The eShopOnContainers helm folder.</span></span>

<span data-ttu-id="acd3f-133">每個個別元件都是使用`helm install`命令來安裝。</span><span class="sxs-lookup"><span data-stu-id="acd3f-133">Each individual component is installed using a `helm install` command.</span></span> <span data-ttu-id="acd3f-134">eShop 包含「部署所有」腳本，它會迴圈執行並使用其各自的 helm 圖表來安裝元件。</span><span class="sxs-lookup"><span data-stu-id="acd3f-134">eShop includes a "deploy all" script that loops through and installs the components using their respective helm charts.</span></span> <span data-ttu-id="acd3f-135">結果是可重複的程式，在原始檔控制中使用應用程式進行版本設定，而小組中的任何人都可以使用單行指令碼命令，部署到 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="acd3f-135">The result is a repeatable process, versioned with the application in source control, that anyone on the team can deploy to an AKS cluster with a one-line script command.</span></span>

> <span data-ttu-id="acd3f-136">請注意，Helm 的第3版已正式移除 Tiller 伺服器元件的需求。</span><span class="sxs-lookup"><span data-stu-id="acd3f-136">Note that version 3 of Helm officially removes the need for the Tiller server component.</span></span> <span data-ttu-id="acd3f-137">如需這項增強功能的詳細資訊，請參閱[這裡](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714)。</span><span class="sxs-lookup"><span data-stu-id="acd3f-137">More information on this enhancement can be found [here](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714).</span></span>

## <a name="azure-dev-spaces"></a><span data-ttu-id="acd3f-138">Azure 開發人員空間</span><span class="sxs-lookup"><span data-stu-id="acd3f-138">Azure Dev Spaces</span></span>

<span data-ttu-id="acd3f-139">雲端原生應用程式可能很快就會變得很大，而且需要大量計算資源才能執行。</span><span class="sxs-lookup"><span data-stu-id="acd3f-139">Cloud-native applications can quickly grow large and complex, requiring significant compute resources to run.</span></span> <span data-ttu-id="acd3f-140">在這些情況下，整個應用程式無法裝載于開發電腦（特別是膝上型電腦）上。</span><span class="sxs-lookup"><span data-stu-id="acd3f-140">In these scenarios, the entire application can't be hosted on a development machine (especially a laptop).</span></span> <span data-ttu-id="acd3f-141">Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="acd3f-141">Azure Dev Spaces is designed to address this problem using AKS.</span></span> <span data-ttu-id="acd3f-142">它可讓開發人員使用其服務的本機版本，同時在 AKS 開發叢集中裝載應用程式的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="acd3f-142">It enables developers to work with a local version of their services while hosting the rest of the application in an AKS development cluster.</span></span>

<span data-ttu-id="acd3f-143">開發人員會在包含整個容器化應用程式的 AKS 叢集中共用執行中（開發）實例。</span><span class="sxs-lookup"><span data-stu-id="acd3f-143">Developers share a running (development) instance in an AKS cluster that contains the entire containerized application.</span></span> <span data-ttu-id="acd3f-144">但他們會在其電腦上使用個人空間設定，以在本機開發其服務。</span><span class="sxs-lookup"><span data-stu-id="acd3f-144">But they use personal spaces set up on their machine to locally develop their services.</span></span> <span data-ttu-id="acd3f-145">準備好時，他們會在 AKS 叢集中從端對端測試，而不會複寫相依性。</span><span class="sxs-lookup"><span data-stu-id="acd3f-145">When ready, they test from end-to-end in the AKS cluster - without replicating dependencies.</span></span> <span data-ttu-id="acd3f-146">Azure Dev Spaces 會將本機電腦的程式碼與 AKS 中的服務合併。</span><span class="sxs-lookup"><span data-stu-id="acd3f-146">Azure Dev Spaces merges code from the local machine with services in AKS.</span></span> <span data-ttu-id="acd3f-147">小組成員可以查看他們的變更在實際 AKS 環境中的行為。</span><span class="sxs-lookup"><span data-stu-id="acd3f-147">Team members can see how their changes will behave in a real AKS environment.</span></span> <span data-ttu-id="acd3f-148">開發人員可以使用 Visual Studio 2017 或 Visual Studio Code，直接在 Kubernetes 中快速反復查看和偵錯工具代碼。</span><span class="sxs-lookup"><span data-stu-id="acd3f-148">Developers can rapidly iterate and debug code directly in Kubernetes using Visual Studio 2017 or Visual Studio Code.</span></span>

<span data-ttu-id="acd3f-149">在圖2-7 中，您可以看到開發人員 Susie 已將更新版的自行車微服務部署到其開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="acd3f-149">In Figure 2-7, you can see that Developer Susie has deployed an updated version of the Bikes microservice into her dev space.</span></span> <span data-ttu-id="acd3f-150">然後她就能夠使用自訂 URL （以她的空間名稱（susie.s.dev.myapp.eus.azds.io）開頭）來測試她的變更。</span><span class="sxs-lookup"><span data-stu-id="acd3f-150">She's then able to test her changes using a custom URL starting with the name of her space (susie.s.dev.myapp.eus.azds.io).</span></span>

<span data-ttu-id="acd3f-151">![eShopOnContainers 架構](./media/azure-devspaces-one.png)
**圖 2-7**。</span><span class="sxs-lookup"><span data-stu-id="acd3f-151">![eShopOnContainers Architecture](./media/azure-devspaces-one.png)
**Figure 2-7**.</span></span> <span data-ttu-id="acd3f-152">開發人員 Susie 會部署自己的自行車微服務版本，並加以測試。</span><span class="sxs-lookup"><span data-stu-id="acd3f-152">Developer Susie deploys her own version of the Bikes microservice and tests it.</span></span>

<span data-ttu-id="acd3f-153">同時，開發人員 John 會自訂保留微服務，並需要測試其變更。</span><span class="sxs-lookup"><span data-stu-id="acd3f-153">At the same time, developer John is customizing the Reservations microservice and needs to test his changes.</span></span> <span data-ttu-id="acd3f-154">他會將自己的變更部署到自己的開發人員空間，而不會與 Susie 的變更相衝突，如圖2-8 所示。</span><span class="sxs-lookup"><span data-stu-id="acd3f-154">He deploys his changes to his own dev space without conflicting with Susie's changes as shown in Figure 2-8.</span></span> <span data-ttu-id="acd3f-155">John 接著會使用自己的 URL （前面加上他的空間名稱（john.s.dev.myapp.eus.azds.io））來測試他的變更。</span><span class="sxs-lookup"><span data-stu-id="acd3f-155">John then tests his changes using his own URL that is prefixed with the name of his space (john.s.dev.myapp.eus.azds.io).</span></span>

<span data-ttu-id="acd3f-156">![eShopOnContainers 架構](./media/azure-devspaces-two.png)
**圖 2-8**。</span><span class="sxs-lookup"><span data-stu-id="acd3f-156">![eShopOnContainers Architecture](./media/azure-devspaces-two.png)
**Figure 2-8**.</span></span> <span data-ttu-id="acd3f-157">開發人員 John 會部署自己的保留微服務版本，並測試它，而不會與其他開發人員衝突。</span><span class="sxs-lookup"><span data-stu-id="acd3f-157">Developer John deploys his own version of the Reservations microservice and tests it without conflicting with other developers.</span></span>

<span data-ttu-id="acd3f-158">使用 Azure Dev Spaces，小組可以直接處理 AKS，同時獨立變更、部署和測試其變更。</span><span class="sxs-lookup"><span data-stu-id="acd3f-158">Using Azure Dev Spaces, teams can work directly with AKS while independently changing, deploying, and testing their changes.</span></span> <span data-ttu-id="acd3f-159">這種方法可減少個別專用託管環境的需求，因為每位開發人員實際上都有自己的 AKS 環境。</span><span class="sxs-lookup"><span data-stu-id="acd3f-159">This approach reduces the need for separate dedicated hosted environments since every developer effectively has their own AKS environment.</span></span> <span data-ttu-id="acd3f-160">開發人員可以使用其 CLI 來處理 Azure Dev Spaces，或啟動其應用程式直接從 Visual Studio Azure Dev Spaces。</span><span class="sxs-lookup"><span data-stu-id="acd3f-160">Developers can work with Azure Dev Spaces using its CLI or launch their application to Azure Dev Spaces directly from Visual Studio.</span></span> [<span data-ttu-id="acd3f-161">深入瞭解 Azure Dev Spaces 的運作方式和設定。</span><span class="sxs-lookup"><span data-stu-id="acd3f-161">Learn more about how Azure Dev Spaces works and is configured.</span></span>](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a><span data-ttu-id="acd3f-162">Azure Functions 和 Logic Apps （無伺服器）</span><span class="sxs-lookup"><span data-stu-id="acd3f-162">Azure Functions and Logic Apps (Serverless)</span></span>

<span data-ttu-id="acd3f-163">EShopOnContainers 範例包含追蹤線上行銷活動的支援。</span><span class="sxs-lookup"><span data-stu-id="acd3f-163">The eShopOnContainers sample includes support for tracking online marketing campaigns.</span></span> <span data-ttu-id="acd3f-164">Azure 函式可用來追蹤指定之行銷活動識別碼的行銷活動詳細資料。</span><span class="sxs-lookup"><span data-stu-id="acd3f-164">An Azure Function is used to track marketing campaign details for a given campaign ID.</span></span> <span data-ttu-id="acd3f-165">單一 Azure 函式比較簡單且足夠，而不是建立完整的微服務。</span><span class="sxs-lookup"><span data-stu-id="acd3f-165">Rather than creating a full microservice, a single Azure Function is simpler and sufficient.</span></span> <span data-ttu-id="acd3f-166">Azure Functions 具有簡單的組建和部署模型，特別是當設定為在 Kubernetes 中執行時。</span><span class="sxs-lookup"><span data-stu-id="acd3f-166">Azure Functions have a simple build and deployment model, especially when configured to run in Kubernetes.</span></span> <span data-ttu-id="acd3f-167">部署函式的功能是使用 Azure Resource Manager （ARM）範本和 Azure CLI。</span><span class="sxs-lookup"><span data-stu-id="acd3f-167">Deploying the function is scripted using Azure Resource Manager (ARM) templates and the Azure CLI.</span></span> <span data-ttu-id="acd3f-168">此活動服務不是面向客戶，而且會叫用單一作業，使其成為 Azure Functions 的絕佳候選項目。</span><span class="sxs-lookup"><span data-stu-id="acd3f-168">This campaign service isn't customer-facing and invokes a single operation, making it a great candidate for Azure Functions.</span></span> <span data-ttu-id="acd3f-169">函數需要最少的設定，包括資料庫連接字串資料和影像基底 URI 設定。</span><span class="sxs-lookup"><span data-stu-id="acd3f-169">The function requires minimal configuration, including a database connection string data and image base URI settings.</span></span> <span data-ttu-id="acd3f-170">您會在 Azure 入口網站中設定 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="acd3f-170">You configure Azure Functions in the Azure portal.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="acd3f-171">[上一頁](map-eshoponcontainers-azure-services.md)
>[下一頁](centralized-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="acd3f-171">[Previous](map-eshoponcontainers-azure-services.md)
[Next](centralized-configuration.md)</span></span>
