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
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="6a0c1-103">雲端原生應用程式套件組合</span><span class="sxs-lookup"><span data-stu-id="6a0c1-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="6a0c1-104">雲端原生應用程式的重要屬性是，它們會利用雲端的功能來加速開發。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="6a0c1-105">這種設計通常表示完整的應用程式會使用不同種類的技術。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="6a0c1-106">應用程式可能會在 Docker 容器中運送，某些服務可能會使用 Azure Functions，而其他元件則可直接在使用硬體 GPU 加速配置於大型裸機伺服器上的虛擬機器上執行。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="6a0c1-107">沒有兩個雲端原生應用程式相同，因此很難提供單一機制來傳送它們。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="6a0c1-108">Docker 容器可以使用 Helm 圖表進行部署，以在 Kubernetes 上執行。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="6a0c1-109">Azure Functions 可以使用 Terraform 範本進行配置。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="6a0c1-110">最後，您可以使用 Terraform 來配置虛擬機器，但使用 Ansible 來建立。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="6a0c1-111">這是一項完整的技術，而且沒有辦法將它們全部封裝成合理的封裝。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="6a0c1-112">直到目前為止。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-112">Until now.</span></span>

<span data-ttu-id="6a0c1-113">雲端原生應用程式套件組合 (CNABs) 是由許多志同道合的公司（例如 Microsoft、Docker 和 HashiCorp）共同作業，以開發將封裝散發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-113">Cloud Native Application Bundles (CNABs) are a joint effort by a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="6a0c1-114">這項工作已在2018年12月宣佈完成，因此仍有相當多的工作要將精力公開給更大的群體。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="6a0c1-115">不過，已經有開啟的 [規格](https://github.com/deislabs/cnab-spec) 和稱為 [Duffle](https://duffle.sh/)的參考實作為參考。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="6a0c1-116">這項工具是以 Go 撰寫的，是 Docker 與 Microsoft 之間的共同工作。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="6a0c1-117">CNABs 可包含不同種類的安裝技術。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="6a0c1-118">這可讓 Helm 圖表、Terraform 範本和 Ansible 的工作手冊等專案並存于相同的套件中。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="6a0c1-119">一旦建立之後，套件就會獨立且可攜;您可以從 USB 杆進行安裝。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="6a0c1-120">系統會以密碼編譯方式簽署套件，以確保它們源自于所宣告的合作物件。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="6a0c1-121">CNAB 的核心是名為的檔案 `bundle.json` 。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="6a0c1-122">此檔案會定義套件組合的內容，其 Terraform 或影像或其他任何內容。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="6a0c1-123">圖11-9 定義叫用某些 Terraform 的 CNAB。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="6a0c1-124">不過請注意，它實際上會定義用來叫用 Terraform 的叫用映射。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="6a0c1-125">封裝之後，位於 *cnab* 目錄中的 docker 檔案會內建于 docker 映射中，並包含在組合中。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="6a0c1-126">將 Terraform 安裝在套件組合中的 Docker 容器內，表示使用者不需要在其電腦上安裝 Terraform 來執行此套件組合。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="6a0c1-127">**圖 10-18** -範例 Terraform 檔</span><span class="sxs-lookup"><span data-stu-id="6a0c1-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="6a0c1-128">`bundle.json`也會定義一組參數，這些參數會傳遞至 Terraform。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="6a0c1-129">組合的參數化可讓您在各種不同的環境中進行安裝。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="6a0c1-130">CNAB 格式也有彈性，因此可用於任何雲端。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="6a0c1-131">它甚至可以用於內部部署解決方案，例如 [OpenStack](https://www.openstack.org/)。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="6a0c1-132">DevOps 決策</span><span class="sxs-lookup"><span data-stu-id="6a0c1-132">DevOps Decisions</span></span>

<span data-ttu-id="6a0c1-133">在 DevOps 的空間中，有許多絕佳的工具可讓您在這幾天內順利完成。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="6a0c1-134">DevOps 旅程入門的最愛書籍是 [Phoenix 專案](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)，它會遵循將虛構公司從 NoOps 轉換為 DevOps 的專案。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="6a0c1-135">其中一件事是針對特定的：部署複雜的雲端原生應用程式時，DevOps 不再是「好的」。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="6a0c1-136">這是一項需求，而且應該在任何專案開始時規劃和資源。</span><span class="sxs-lookup"><span data-stu-id="6a0c1-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="6a0c1-137">參考資料</span><span class="sxs-lookup"><span data-stu-id="6a0c1-137">References</span></span>

- [<span data-ttu-id="6a0c1-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6a0c1-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="6a0c1-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="6a0c1-139">Azure Resource Manager</span></span>](/azure/azure-resource-manager/management/overview)
- [<span data-ttu-id="6a0c1-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="6a0c1-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="6a0c1-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="6a0c1-141">Azure CLI</span></span>](/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="6a0c1-142">[上一個](infrastructure-as-code.md) 
>[下一步](summary.md)</span><span class="sxs-lookup"><span data-stu-id="6a0c1-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
