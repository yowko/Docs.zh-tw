---
title: 容器和 Docker 簡介
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 容器和 Docker 簡介
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c1f78a8904270123188367a01bddbcac3f7f1b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572271"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="b689f-103">容器和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="b689f-103">Introduction to Containers and Docker</span></span>

<span data-ttu-id="b689f-104">容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起，成為一個容器映像。</span><span class="sxs-lookup"><span data-stu-id="b689f-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="b689f-105">容器化應用程式可以當作一個單位來測試，並以容器映像執行個體形式部署至主機作業系統 (OS)。</span><span class="sxs-lookup"><span data-stu-id="b689f-105">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="b689f-106">就像是貨櫃允許利用船隻、火車或貨車運輸貨物，而不論內含哪種貨物，軟體容器是軟體的標準單位，可包含不同的程式碼和相依性。</span><span class="sxs-lookup"><span data-stu-id="b689f-106">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="b689f-107">以此方式容器化軟體可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境進行部署。</span><span class="sxs-lookup"><span data-stu-id="b689f-107">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="b689f-108">容器也可讓不同的應用程式在共用 OS 上彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="b689f-108">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="b689f-109">容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。</span><span class="sxs-lookup"><span data-stu-id="b689f-109">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="b689f-110">因此，容器所需空間明顯小於虛擬機器 (VM) 映像。</span><span class="sxs-lookup"><span data-stu-id="b689f-110">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="b689f-111">每個容器可以執行整個 Web 應用程式或服務，如圖 2-1 所示。</span><span class="sxs-lookup"><span data-stu-id="b689f-111">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="b689f-112">在此範例中，Docker 主機是容器主機，而 App1、App2、Svc 1 和 Svc 2 是容器化應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="b689f-112">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="b689f-113">**圖 2-1**.</span><span class="sxs-lookup"><span data-stu-id="b689f-113">**Figure 2-1**.</span></span> <span data-ttu-id="b689f-114">在容器主機上執行的多個容器</span><span class="sxs-lookup"><span data-stu-id="b689f-114">Multiple containers running on a container host</span></span>

<span data-ttu-id="b689f-115">容器化的另一個優點是延展性。</span><span class="sxs-lookup"><span data-stu-id="b689f-115">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="b689f-116">您可以針對短期工作建立新的容器，以更快擴充。</span><span class="sxs-lookup"><span data-stu-id="b689f-116">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="b689f-117">從應用程式的觀點來看，具現化映像 (建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="b689f-117">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="b689f-118">不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。</span><span class="sxs-lookup"><span data-stu-id="b689f-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="b689f-119">簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。</span><span class="sxs-lookup"><span data-stu-id="b689f-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="b689f-120">最重要的優點是為開發與作業提供隔離。</span><span class="sxs-lookup"><span data-stu-id="b689f-120">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b689f-121">[上一個] (../index.md) [下一個] (docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="b689f-121">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
