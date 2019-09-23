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
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="b47a4-103">雲端原生應用程式套件組合</span><span class="sxs-lookup"><span data-stu-id="b47a4-103">Cloud Native Application Bundles</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b47a4-104">雲端原生應用程式的重要屬性是，它們會利用雲端的屬性來加速開發。</span><span class="sxs-lookup"><span data-stu-id="b47a4-104">A key property of cloud-native applications is that they leverage the properties of the cloud to speed up development.</span></span> <span data-ttu-id="b47a4-105">這通常表示完整的應用程式會使用不同種類的技術。</span><span class="sxs-lookup"><span data-stu-id="b47a4-105">This often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="b47a4-106">應用程式可能會隨附在 Docker 容器中，有些服務可能會使用 Azure Functions 而其他部分則可直接在使用硬體 GPU 加速在大型金屬伺服器上配置的虛擬機器上執行。</span><span class="sxs-lookup"><span data-stu-id="b47a4-106">Applications may be shipped in Docker containers, some services may use Azure Functions while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="b47a4-107">沒有兩個雲端原生應用程式相同，因此很難以提供傳送它們的單一機制。</span><span class="sxs-lookup"><span data-stu-id="b47a4-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="b47a4-108">Docker 容器可在 Kubernetes 上執行，並使用 Helm 圖表進行部署。</span><span class="sxs-lookup"><span data-stu-id="b47a4-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="b47a4-109">Azure Functions 可以使用 Terraform 範本進行配置。</span><span class="sxs-lookup"><span data-stu-id="b47a4-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="b47a4-110">最後，您可以使用 Terraform 來配置虛擬機器，但使用 Ansible 來建立。</span><span class="sxs-lookup"><span data-stu-id="b47a4-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="b47a4-111">這是一項完整的技術，而且沒有辦法將它們全部封裝在一起，成為合理的套件。</span><span class="sxs-lookup"><span data-stu-id="b47a4-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="b47a4-112">到目前為止。</span><span class="sxs-lookup"><span data-stu-id="b47a4-112">Until now.</span></span>

<span data-ttu-id="b47a4-113">雲端原生應用程式套件組合（CNABs）是許多意識公司（例如 Microsoft、Docker 和 HashiCorp）的共同工作，可開發用來封裝分散式應用程式的規格。</span><span class="sxs-lookup"><span data-stu-id="b47a4-113">Cloud Native Application Bundles (CNABs) are a joint effort of a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="b47a4-114">這項工作是在2018年12月宣佈的，因此，仍然需要執行一項工作，將工作暴露于更大的社區。</span><span class="sxs-lookup"><span data-stu-id="b47a4-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="b47a4-115">不過，已經有[開放式規格](https://github.com/deislabs/cnab-spec)和參考實，稱為[行李](https://duffle.sh/)。</span><span class="sxs-lookup"><span data-stu-id="b47a4-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="b47a4-116">這項工具是以 Go 撰寫，這是 Docker 與 Microsoft 之間的共同投入。</span><span class="sxs-lookup"><span data-stu-id="b47a4-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="b47a4-117">CNABs 可以包含不同種類的安裝技術。</span><span class="sxs-lookup"><span data-stu-id="b47a4-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="b47a4-118">如此一來，Helm 圖、Terraform 範本和 Ansible 的操作手冊就可以並存于相同的套件中。</span><span class="sxs-lookup"><span data-stu-id="b47a4-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="b47a4-119">建立之後，套件是獨立且可移植的;您可以從 USB 卡安裝它們。</span><span class="sxs-lookup"><span data-stu-id="b47a4-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="b47a4-120">系統會以密碼編譯方式簽署套件，以確保它們源自于其宣告的合作物件。</span><span class="sxs-lookup"><span data-stu-id="b47a4-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="b47a4-121">CNAB 的核心是名`bundle.json`為的檔案。</span><span class="sxs-lookup"><span data-stu-id="b47a4-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="b47a4-122">此檔案會定義組合的內容，其 Terraform 或影像，或其他任何專案。</span><span class="sxs-lookup"><span data-stu-id="b47a4-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="b47a4-123">圖11-9 定義了叫用一些 Terraform 的 CNAB。</span><span class="sxs-lookup"><span data-stu-id="b47a4-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="b47a4-124">不過，請注意，它實際上會定義用來叫用 Terraform 的調用影像。</span><span class="sxs-lookup"><span data-stu-id="b47a4-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="b47a4-125">當封裝時，位於*cnab*目錄中的 docker 檔案會內建到 docker 映射中，並包含在組合中。</span><span class="sxs-lookup"><span data-stu-id="b47a4-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="b47a4-126">將 Terraform 安裝在配套中的 Docker 容器內，表示使用者不需要在其電腦上安裝 Terraform 來執行配套。</span><span class="sxs-lookup"><span data-stu-id="b47a4-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="b47a4-127">**圖 11-13** -範例 Terraform 檔案</span><span class="sxs-lookup"><span data-stu-id="b47a4-127">**Figure 11-13** - An example Terraform file</span></span>

<span data-ttu-id="b47a4-128">`bundle.json`也會定義一組傳遞至 Terraform 的參數。</span><span class="sxs-lookup"><span data-stu-id="b47a4-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="b47a4-129">組合的參數化可讓您在各種不同的環境中安裝。</span><span class="sxs-lookup"><span data-stu-id="b47a4-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="b47a4-130">CNAB 格式也有彈性，讓它可用於任何雲端。</span><span class="sxs-lookup"><span data-stu-id="b47a4-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="b47a4-131">它甚至可以用於內部部署解決方案，例如[OpenStack](https://www.openstack.org/)。</span><span class="sxs-lookup"><span data-stu-id="b47a4-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="b47a4-132">DevOps 決策</span><span class="sxs-lookup"><span data-stu-id="b47a4-132">DevOps Decisions</span></span>

<span data-ttu-id="b47a4-133">在 DevOps 的空間中，有很多絕佳的工具可讓您順利完成。</span><span class="sxs-lookup"><span data-stu-id="b47a4-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="b47a4-134">開始使用 DevOps 旅程的最愛書是[Phoenix 專案](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)，其遵循將虛構公司從 NoOps 轉換為 DevOps。</span><span class="sxs-lookup"><span data-stu-id="b47a4-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="b47a4-135">其中一件事是：部署複雜的雲端原生應用程式時，DevOps 不再是「不錯的」。</span><span class="sxs-lookup"><span data-stu-id="b47a4-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="b47a4-136">這是一項需求，而且應該在任何專案開始時規劃和資源。</span><span class="sxs-lookup"><span data-stu-id="b47a4-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b47a4-137">上一步</span><span class="sxs-lookup"><span data-stu-id="b47a4-137">Previous</span></span>](infrastructure-as-code.md)
