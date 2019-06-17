---
title: 容器和 Docker 簡介
description: 取得使用 Docker 主要優點的高階概觀。
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644949"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="70cc7-103">容器和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="70cc7-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="70cc7-104">容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起成為一個容器映像。您可以將容器化應用程式當作一個單位來測試，並將它以容器映像執行個體形式部署至主機作業系統 (OS)。</span><span class="sxs-lookup"><span data-stu-id="70cc7-104">*Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image. You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system (OS).*</span></span>

<span data-ttu-id="70cc7-105">就像是貨櫃允許利用船隻、火車或貨車運輸貨物，而不論內含哪種貨物，軟體容器是軟體部署的標準單位，可包含不同的程式碼和相依性。</span><span class="sxs-lookup"><span data-stu-id="70cc7-105">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="70cc7-106">以此方式容器化軟體可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境進行部署。</span><span class="sxs-lookup"><span data-stu-id="70cc7-106">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="70cc7-107">容器也可讓不同的應用程式在共用 OS 上彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="70cc7-107">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="70cc7-108">容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。</span><span class="sxs-lookup"><span data-stu-id="70cc7-108">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="70cc7-109">因此，容器所需磁碟使用量小於虛擬機器 (VM) 映像。</span><span class="sxs-lookup"><span data-stu-id="70cc7-109">Containers therefore have a much smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="70cc7-110">每個容器可以執行整個 Web 應用程式或服務，如圖 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="70cc7-110">Each container can run a whole web application or a service, as shown in Figure 1-1.</span></span> <span data-ttu-id="70cc7-111">在此範例中，Docker 主機是容器主機，而 App1、App2、Svc1 及 Svc2 是容器化應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="70cc7-111">In this example, Docker host is a container host, and App1, App2, Svc1, and Svc2 are containerized applications or services.</span></span>

![在 VM 或實體伺服器的作業系統上執行的兩個應用程式和兩個服務](./media/image1.png)

<span data-ttu-id="70cc7-113">**圖 1-1**。</span><span class="sxs-lookup"><span data-stu-id="70cc7-113">**Figure 1-1**.</span></span> <span data-ttu-id="70cc7-114">在容器主機上執行的多個容器</span><span class="sxs-lookup"><span data-stu-id="70cc7-114">Multiple containers running on a container host</span></span>

<span data-ttu-id="70cc7-115">您可以從容器化衍生的另一個優點是延展性。</span><span class="sxs-lookup"><span data-stu-id="70cc7-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="70cc7-116">您可以針對短期工作建立新的容器，以更快擴充。</span><span class="sxs-lookup"><span data-stu-id="70cc7-116">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="70cc7-117">從應用程式的觀點來看，具現化映像 (建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="70cc7-117">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="70cc7-118">不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。</span><span class="sxs-lookup"><span data-stu-id="70cc7-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="70cc7-119">簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。</span><span class="sxs-lookup"><span data-stu-id="70cc7-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application lifecycle workflow.</span></span> <span data-ttu-id="70cc7-120">最重要的優點是可為開發與作業提供環境隔離。</span><span class="sxs-lookup"><span data-stu-id="70cc7-120">The most important benefit is the environment isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="70cc7-121">下一步</span><span class="sxs-lookup"><span data-stu-id="70cc7-121">Next</span></span>](what-is-docker.md)
