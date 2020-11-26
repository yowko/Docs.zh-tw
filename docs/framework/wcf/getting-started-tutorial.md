---
title: 教學課程：開始使用 Windows Communication Foundation 應用程式
description: 這些教學課程提供建立 WCF 應用程式的簡介。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238232"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="c0339-103">教學課程：開始使用 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="c0339-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>

<span data-ttu-id="c0339-104">下列一系列的教學課程將為您介紹 Windows Communication Foundation (WCF) 程式設計體驗。</span><span class="sxs-lookup"><span data-stu-id="c0339-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="c0339-105">依序執行這些教學課程可讓您瞭解建立 WCF 應用程式所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="c0339-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="c0339-106">完成之後，您將會有執行中的 WCF 服務和呼叫服務的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="c0339-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="c0339-107">本教學課程假設您使用 Visual Studio 作為開發環境。</span><span class="sxs-lookup"><span data-stu-id="c0339-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="c0339-108">如果您使用的是其他開發環境，請忽略 Visual Studio 特定的指示。</span><span class="sxs-lookup"><span data-stu-id="c0339-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="c0339-109">如需可供下載並執行的 WCF 應用程式範例，請參閱 [Windows Communication Foundation 範例](samples/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c0339-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="c0339-110">如需範例的簡介，請參閱使用者 [入門範例](samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c0339-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="c0339-111">如需有關建立服務和用戶端的更深入資訊，請參閱 [基本 WCF 程式設計](basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="c0339-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="c0339-112">WCF 教學課程</span><span class="sxs-lookup"><span data-stu-id="c0339-112">WCF tutorials</span></span>

<span data-ttu-id="c0339-113">前三個教學課程將說明如何定義 WCF 服務合約、如何執行它，以及如何裝載它。</span><span class="sxs-lookup"><span data-stu-id="c0339-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="c0339-114">您所建立的服務會在主控台應用程式中自我裝載。</span><span class="sxs-lookup"><span data-stu-id="c0339-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="c0339-115">您也可以在 Microsoft Internet Information Services (IIS) 上裝載服務。</span><span class="sxs-lookup"><span data-stu-id="c0339-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="c0339-116">如需詳細資訊，請參閱 [如何：在 IIS 中裝載 WCF 服務](feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="c0339-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="c0339-117">雖然您在教學課程中使用程式碼來設定服務，但是您也可以在 [設定檔中設定服務](configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c0339-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="c0339-118">教學課程：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="c0339-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="c0339-119">您可以使用使用者定義的介面來建立 WCF 合約。</span><span class="sxs-lookup"><span data-stu-id="c0339-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="c0339-120">此合約會定義服務所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="c0339-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="c0339-121">教學課程：執行服務合約</span><span class="sxs-lookup"><span data-stu-id="c0339-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="c0339-122">定義合約之後，您必須使用服務類別來執行它。</span><span class="sxs-lookup"><span data-stu-id="c0339-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="c0339-123">教學課程：裝載和執行基本服務</span><span class="sxs-lookup"><span data-stu-id="c0339-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="c0339-124">設定服務的端點，並在主控台應用程式中裝載服務。</span><span class="sxs-lookup"><span data-stu-id="c0339-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="c0339-125">若要讓服務成為使用中，您必須在執行時間環境內進行設定，並將其裝載在執行時間環境中。</span><span class="sxs-lookup"><span data-stu-id="c0339-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="c0339-126">此執行時間環境會建立服務並控制其內容和存留期。</span><span class="sxs-lookup"><span data-stu-id="c0339-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="c0339-127">接下來的兩個教學課程將說明如何建立、設定及使用用戶端應用程式，以呼叫服務所公開的作業。</span><span class="sxs-lookup"><span data-stu-id="c0339-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="c0339-128">服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c0339-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="c0339-129">Visual Studio 會將存取此中繼資料的程式自動化，並使用它來建立服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0339-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="c0339-130">如果您決定不使用 Visual Studio，可以改為使用 [ [System.servicemodel 中繼資料公用程式] 工具 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) 。</span><span class="sxs-lookup"><span data-stu-id="c0339-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="c0339-131">教學課程：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="c0339-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="c0339-132">從 WCF 服務取出用來建立 WCF 用戶端 proxy 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c0339-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="c0339-133">您可以使用 Visual Studio 來取得中繼資料來新增服務參考，也可以使用 [System.servicemodel 中繼資料公用程式] 工具。</span><span class="sxs-lookup"><span data-stu-id="c0339-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="c0339-134">您可以指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="c0339-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="c0339-135">教學課程：使用用戶端</span><span class="sxs-lookup"><span data-stu-id="c0339-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="c0339-136">使用 WCF 用戶端 proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="c0339-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="c0339-137">參考</span><span class="sxs-lookup"><span data-stu-id="c0339-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="c0339-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0339-138">See also</span></span>

- [<span data-ttu-id="c0339-139">概念總覽</span><span class="sxs-lookup"><span data-stu-id="c0339-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="c0339-140">檔指南</span><span class="sxs-lookup"><span data-stu-id="c0339-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="c0339-141">什麼是 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c0339-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="c0339-142">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0339-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="c0339-143">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="c0339-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="c0339-144">建立用戶端</span><span class="sxs-lookup"><span data-stu-id="c0339-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="c0339-145">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="c0339-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="c0339-146">如何：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="c0339-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="c0339-147">How to：使用雙工合約存取服務</span><span class="sxs-lookup"><span data-stu-id="c0339-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="c0339-148">System.servicemodel 中繼資料公用程式工具 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="c0339-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="c0339-149">如何：使用 Svcutil.exe 下載元資料檔案</span><span class="sxs-lookup"><span data-stu-id="c0339-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="c0339-150">如何：使用設定檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="c0339-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="c0339-151">使用系結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="c0339-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c0339-152">開始使用範例</span><span class="sxs-lookup"><span data-stu-id="c0339-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="c0339-153">Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="c0339-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="c0339-154">自我裝載</span><span class="sxs-lookup"><span data-stu-id="c0339-154">Self-Host</span></span>](samples/self-host.md)
