---
title: 容器和 Docker 簡介
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c2a6b9802bbb995939d33c5c40ef9c1afa1620e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148817"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="d47a8-103">容器和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="d47a8-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="d47a8-104">容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起，成為一個容器映像。</span><span class="sxs-lookup"><span data-stu-id="d47a8-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="d47a8-105">您可以將容器化應用程式當作一個單位來測試，並將它以容器映像執行個體形式部署至主機作業系統。</span><span class="sxs-lookup"><span data-stu-id="d47a8-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="d47a8-106">就像運輸業使用標準化貨櫃以透過船隻、火車或貨車移動貨物，而不論其內的貨物，軟體容器都是標準軟體單位，可包含不同的程式碼和相依性。</span><span class="sxs-lookup"><span data-stu-id="d47a8-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="d47a8-107">將軟體放置到容器可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境部署這些容器。</span><span class="sxs-lookup"><span data-stu-id="d47a8-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="d47a8-108">容器也可讓不同的應用程式在共用作業系統 (OS) 上彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="d47a8-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="d47a8-109">容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。</span><span class="sxs-lookup"><span data-stu-id="d47a8-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="d47a8-110">因此，容器所需空間明顯小於虛擬機器 (VM) 映像。</span><span class="sxs-lookup"><span data-stu-id="d47a8-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="d47a8-111">每個容器都可以執行整個 Web 應用程式或服務，如圖 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="d47a8-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="d47a8-112">圖 1-1:在容器主機上執行的多個容器</span><span class="sxs-lookup"><span data-stu-id="d47a8-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="d47a8-113">在此範例中，Docker 主機是容器主機，而 App 1、App 2、Svc 1 和 Svc 2 是容器化應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="d47a8-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="d47a8-114">您可以從容器化衍生的另一個優點是延展性。</span><span class="sxs-lookup"><span data-stu-id="d47a8-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="d47a8-115">針對短期工作建立新的容器，即可更快速地擴充。</span><span class="sxs-lookup"><span data-stu-id="d47a8-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="d47a8-116">從應用程式的觀點來看，「具現化映像」(建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="d47a8-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="d47a8-117">可靠性，不過，當您執行的相同映像的多個執行個體在多部主機伺服器，通常要為每個容器 （映像執行個體），在不同的主機伺服器中執行或在不同容錯網域中的 VM。</span><span class="sxs-lookup"><span data-stu-id="d47a8-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="d47a8-118">簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。</span><span class="sxs-lookup"><span data-stu-id="d47a8-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="d47a8-119">最重要的優點是為開發與作業提供隔離。</span><span class="sxs-lookup"><span data-stu-id="d47a8-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d47a8-120">下一步</span><span class="sxs-lookup"><span data-stu-id="d47a8-120">Next</span></span>](what-is-docker.md)