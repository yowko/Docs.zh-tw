---
title: 容器和 Docker 簡介
description: 取得使用 Docker 的主要優點的高層級概觀。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: aa3ead1cb184e23dd091822368e62f580ed73ee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785618"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="ebb99-103">容器和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="ebb99-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="ebb99-104">*容器化是在其中應用程式或服務、 其相依性和及其組態 （抽象化為部署資訊清單檔案） 會封裝在一起成為容器映像的軟體開發方法。然後可以測試當做一個單位的容器化應用程式並將它部署為主機作業系統 (OS) 的容器映像執行個體。*</span><span class="sxs-lookup"><span data-stu-id="ebb99-104">*Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image. You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system (OS).*</span></span>

<span data-ttu-id="ebb99-105">就像是貨櫃允許利用船隻、火車或貨車運輸貨物，而不論內含哪種貨物，軟體容器是軟體部署的標準單位，可包含不同的程式碼和相依性。</span><span class="sxs-lookup"><span data-stu-id="ebb99-105">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="ebb99-106">以此方式容器化軟體可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境進行部署。</span><span class="sxs-lookup"><span data-stu-id="ebb99-106">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="ebb99-107">容器也可讓不同的應用程式在共用 OS 上彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="ebb99-107">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="ebb99-108">容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。</span><span class="sxs-lookup"><span data-stu-id="ebb99-108">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="ebb99-109">因此，容器所小使用量虛擬機器 (VM) 映像。</span><span class="sxs-lookup"><span data-stu-id="ebb99-109">Containers therefore have a much smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="ebb99-110">每個容器可以執行整個 web 應用程式或服務，如所示的圖 1-1。</span><span class="sxs-lookup"><span data-stu-id="ebb99-110">Each container can run a whole web application or a service, as shown in Figure 1-1.</span></span> <span data-ttu-id="ebb99-111">在此範例中，Docker 主機是容器主機，而 App1、 App2、 Svc1 和 Svc2 是容器化應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="ebb99-111">In this example, Docker host is a container host, and App1, App2, Svc1, and Svc2 are containerized applications or services.</span></span>

![在 VM 或實體伺服器的作業系統上執行的兩個應用程式和兩個服務](./media/image1.png)

<span data-ttu-id="ebb99-113">**圖 1-1**。</span><span class="sxs-lookup"><span data-stu-id="ebb99-113">**Figure 1-1**.</span></span> <span data-ttu-id="ebb99-114">在容器主機上執行的多個容器</span><span class="sxs-lookup"><span data-stu-id="ebb99-114">Multiple containers running on a container host</span></span>

<span data-ttu-id="ebb99-115">您可以從容器化衍生的另一個優點是延展性。</span><span class="sxs-lookup"><span data-stu-id="ebb99-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="ebb99-116">您可以針對短期工作建立新的容器，以更快擴充。</span><span class="sxs-lookup"><span data-stu-id="ebb99-116">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="ebb99-117">從應用程式的觀點來看，具現化映像 (建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="ebb99-117">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="ebb99-118">不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。</span><span class="sxs-lookup"><span data-stu-id="ebb99-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="ebb99-119">簡單來說，容器會提供隔離、 可攜性、 靈活性、 延展性和控制的優點，在整個應用程式生命週期工作流程。</span><span class="sxs-lookup"><span data-stu-id="ebb99-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application lifecycle workflow.</span></span> <span data-ttu-id="ebb99-120">最重要的優點是開發與營運部門提供環境隔離。</span><span class="sxs-lookup"><span data-stu-id="ebb99-120">The most important benefit is the environment isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="ebb99-121">下一步</span><span class="sxs-lookup"><span data-stu-id="ebb99-121">Next</span></span>](what-is-docker.md)
