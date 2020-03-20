---
title: 教程：開始使用 Windows 通信基礎應用程式
description: 這些教程提供了創建 WCF 應用程式的介紹。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184115"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="f1238-103">教程：開始使用 Windows 通信基礎應用程式</span><span class="sxs-lookup"><span data-stu-id="f1238-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="f1238-104">以下一系列教程將向您介紹 Windows 通信基礎 （WCF） 程式設計體驗。</span><span class="sxs-lookup"><span data-stu-id="f1238-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="f1238-105">按順序完成這些教程將為您提供對創建 WCF 應用程式所需的步驟的介紹性理解。</span><span class="sxs-lookup"><span data-stu-id="f1238-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="f1238-106">完成後，您將有一個正在運行的 WCF 服務和一個 WCF 用戶端調用該服務。</span><span class="sxs-lookup"><span data-stu-id="f1238-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="f1238-107">本教程假定您正在使用 Visual Studio 作為開發環境。</span><span class="sxs-lookup"><span data-stu-id="f1238-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="f1238-108">如果您正在使用其他開發環境，請忽略特定于 Visual Studio 的說明。</span><span class="sxs-lookup"><span data-stu-id="f1238-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="f1238-109">有關可以下載和運行的示例 WCF 應用程式，請參閱[Windows 通信基礎示例](samples/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f1238-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="f1238-110">有關示例的介紹，請參閱[入門示例](samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f1238-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="f1238-111">有關創建服務和用戶端的深入資訊，請參閱[基本 WCF 程式設計](basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="f1238-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="f1238-112">WCF 教程</span><span class="sxs-lookup"><span data-stu-id="f1238-112">WCF tutorials</span></span>

<span data-ttu-id="f1238-113">前三個教程介紹如何定義 WCF 服務協定、如何實現它以及如何託管它。</span><span class="sxs-lookup"><span data-stu-id="f1238-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="f1238-114">您創建的服務在主控台應用程式中自託管。</span><span class="sxs-lookup"><span data-stu-id="f1238-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="f1238-115">您還可以在 Microsoft 互聯網資訊服務 （IIS） 下託管服務。</span><span class="sxs-lookup"><span data-stu-id="f1238-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="f1238-116">有關詳細資訊，請參閱[如何：在 IIS 中託管 WCF 服務](feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="f1238-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="f1238-117">儘管在本教程中使用代碼佈建服務，但您也可以[在設定檔中佈建服務](configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="f1238-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="f1238-118">教程：定義服務協定</span><span class="sxs-lookup"><span data-stu-id="f1238-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="f1238-119">使用使用者定義的介面創建 WCF 協定。</span><span class="sxs-lookup"><span data-stu-id="f1238-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="f1238-120">此協定定義服務公開的功能。</span><span class="sxs-lookup"><span data-stu-id="f1238-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="f1238-121">教程：實現服務合同</span><span class="sxs-lookup"><span data-stu-id="f1238-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="f1238-122">定義協定後，必須使用服務類實現它。</span><span class="sxs-lookup"><span data-stu-id="f1238-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="f1238-123">教程：託管並運行基本服務</span><span class="sxs-lookup"><span data-stu-id="f1238-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="f1238-124">佈建服務的終結點，並在主控台應用程式中託管服務。</span><span class="sxs-lookup"><span data-stu-id="f1238-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="f1238-125">要使服務處於活動狀態，必須配置該服務並在運行時環境中託管它。</span><span class="sxs-lookup"><span data-stu-id="f1238-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="f1238-126">此運行時環境創建服務並控制其上下文和存留期。</span><span class="sxs-lookup"><span data-stu-id="f1238-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="f1238-127">接下來的兩個教程介紹如何創建、配置和使用用戶端應用程式來調用服務公開的操作。</span><span class="sxs-lookup"><span data-stu-id="f1238-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="f1238-128">服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f1238-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="f1238-129">Visual Studio 自動訪問此中繼資料的過程，並用它來構造服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f1238-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="f1238-130">如果您決定不使用 Visual Studio，則可以使用[服務模型中繼資料實用程式工具 （*Svcutil.exe*）。](servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="f1238-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="f1238-131">教程：創建用戶端</span><span class="sxs-lookup"><span data-stu-id="f1238-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="f1238-132">檢索中繼資料以從 WCF 服務創建 WCF 用戶端代理。</span><span class="sxs-lookup"><span data-stu-id="f1238-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="f1238-133">通過使用 Visual Studio 添加服務引用來檢索中繼資料，或者可以使用服務模型中繼資料實用程式工具。</span><span class="sxs-lookup"><span data-stu-id="f1238-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="f1238-134">指定用戶端用於訪問服務的終結點。</span><span class="sxs-lookup"><span data-stu-id="f1238-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="f1238-135">教程：使用用戶端</span><span class="sxs-lookup"><span data-stu-id="f1238-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="f1238-136">使用 WCF 用戶端代理調用服務操作。</span><span class="sxs-lookup"><span data-stu-id="f1238-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="f1238-137">參考</span><span class="sxs-lookup"><span data-stu-id="f1238-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="f1238-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1238-138">See also</span></span>

- [<span data-ttu-id="f1238-139">概念概觀</span><span class="sxs-lookup"><span data-stu-id="f1238-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="f1238-140">文檔指南</span><span class="sxs-lookup"><span data-stu-id="f1238-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="f1238-141">什麼是 Windows 通信基礎</span><span class="sxs-lookup"><span data-stu-id="f1238-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="f1238-142">WCF 功能詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f1238-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="f1238-143">基本程式設計生命週期</span><span class="sxs-lookup"><span data-stu-id="f1238-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="f1238-144">構建用戶端</span><span class="sxs-lookup"><span data-stu-id="f1238-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="f1238-145">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="f1238-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="f1238-146">如何：創建雙工協定</span><span class="sxs-lookup"><span data-stu-id="f1238-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="f1238-147">如何：使用雙工協定訪問服務</span><span class="sxs-lookup"><span data-stu-id="f1238-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="f1238-148">服務模型中繼資料實用程式工具 （Svcutil.exe）</span><span class="sxs-lookup"><span data-stu-id="f1238-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="f1238-149">如何：使用 Svcutil.exe 下載中繼資料文檔</span><span class="sxs-lookup"><span data-stu-id="f1238-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="f1238-150">如何：使用設定檔發佈服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f1238-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f1238-151">使用綁定佈建服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="f1238-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f1238-152">入門示例</span><span class="sxs-lookup"><span data-stu-id="f1238-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="f1238-153">Windows 通信基礎示例</span><span class="sxs-lookup"><span data-stu-id="f1238-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="f1238-154">自我裝載</span><span class="sxs-lookup"><span data-stu-id="f1238-154">Self-Host</span></span>](samples/self-host.md)
