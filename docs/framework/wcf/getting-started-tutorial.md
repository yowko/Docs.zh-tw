---
title: 教學課程：開始使用 Windows Communication Foundation 應用程式
description: 這些教學課程提供建立 WCF 應用程式的簡介。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929536"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="9e55f-103">教學課程：開始使用 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="9e55f-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="9e55f-104">下面一系列教學課程會為您介紹至 Windows Communication Foundation (WCF) 程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="9e55f-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="9e55f-105">透過這些教學課程中順序的工作會提供您建立 WCF 應用程式所需的步驟大致了解。</span><span class="sxs-lookup"><span data-stu-id="9e55f-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="9e55f-106">完成之後，您必須執行的 WCF 服務和 WCF 用戶端呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="9e55f-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span> 

<span data-ttu-id="9e55f-107">此教學課程假設您使用 Visual Studio 作為開發環境。</span><span class="sxs-lookup"><span data-stu-id="9e55f-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="9e55f-108">如果您使用另一個開發環境，請略過 Visual Studio 特定指示。</span><span class="sxs-lookup"><span data-stu-id="9e55f-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span> 

<span data-ttu-id="9e55f-109">您可以下載並執行範例 WCF 應用程式，請參閱 < [Windows Communication Foundation 範例](samples/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9e55f-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="9e55f-110">如需簡介範例，請參閱 <<c0> [ 開始使用範例](samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="9e55f-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="9e55f-111">如需建立服務和用戶端的詳細深入資訊，請參閱 <<c0> [ 基本 WCF 程式設計](basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="9e55f-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="9e55f-112">WCF 的教學課程</span><span class="sxs-lookup"><span data-stu-id="9e55f-112">WCF tutorials</span></span>

<span data-ttu-id="9e55f-113">前三個教學課程說明如何定義 WCF 服務合約、 如何實作它，以及如何裝載它。</span><span class="sxs-lookup"><span data-stu-id="9e55f-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="9e55f-114">您所建立的服務是自我裝載的主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="9e55f-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="9e55f-115">您也可以裝載在 Microsoft Internet Information Services (IIS 服務）。</span><span class="sxs-lookup"><span data-stu-id="9e55f-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="9e55f-116">如需詳細資訊，請參閱[如何：將 WCF 服務裝載於 IIS](feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="9e55f-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="9e55f-117">雖然您可以使用程式碼來設定服務在本教學課程中，您也可以[設定服務組態檔內](configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="9e55f-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span> 

- [<span data-ttu-id="9e55f-118">教學課程：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="9e55f-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="9e55f-119">您可以建立 WCF 合約具有使用者定義的介面。</span><span class="sxs-lookup"><span data-stu-id="9e55f-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="9e55f-120">此合約會定義服務所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="9e55f-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="9e55f-121">教學課程：實作服務合約</span><span class="sxs-lookup"><span data-stu-id="9e55f-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="9e55f-122">定義合約之後，您必須透過服務類別來進行實作。</span><span class="sxs-lookup"><span data-stu-id="9e55f-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="9e55f-123">教學課程：裝載和執行基本的服務</span><span class="sxs-lookup"><span data-stu-id="9e55f-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="9e55f-124">設定服務的端點，並將服務裝載於主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9e55f-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="9e55f-125">服務才會變成作用中，您必須設定它，並裝載在執行階段環境中。</span><span class="sxs-lookup"><span data-stu-id="9e55f-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="9e55f-126">此執行階段環境中建立服務，並控制其內容和存留期。</span><span class="sxs-lookup"><span data-stu-id="9e55f-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="9e55f-127">下面兩個教學課程說明如何建立、 設定和使用用戶端應用程式，來呼叫服務作業公開 （expose）。</span><span class="sxs-lookup"><span data-stu-id="9e55f-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="9e55f-128">服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9e55f-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="9e55f-129">Visual Studio 會存取此中繼資料的程序自動化，並使用它來建構服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="9e55f-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="9e55f-130">如果您決定不使用 Visual Studio，您可以使用[ServiceModel Metadata Utility 工具 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md)改。</span><span class="sxs-lookup"><span data-stu-id="9e55f-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="9e55f-131">教學課程：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="9e55f-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="9e55f-132">擷取從 WCF 服務建立 WCF 用戶端 proxy 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9e55f-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="9e55f-133">您使用 Visual Studio 加入服務參考來擷取中繼資料，或者您可以使用 ServiceModel Metadata Utility 工具。</span><span class="sxs-lookup"><span data-stu-id="9e55f-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="9e55f-134">您指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="9e55f-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="9e55f-135">教學課程：使用用戶端</span><span class="sxs-lookup"><span data-stu-id="9e55f-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="9e55f-136">您可以使用 WCF 用戶端 proxy 來呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="9e55f-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="9e55f-137">參考資料</span><span class="sxs-lookup"><span data-stu-id="9e55f-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="9e55f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e55f-138">See also</span></span>

- [<span data-ttu-id="9e55f-139">概念式概觀</span><span class="sxs-lookup"><span data-stu-id="9e55f-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="9e55f-140">文件指南</span><span class="sxs-lookup"><span data-stu-id="9e55f-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="9e55f-141">什麼是 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9e55f-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="9e55f-142">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e55f-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="9e55f-143">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="9e55f-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="9e55f-144">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="9e55f-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="9e55f-145">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="9e55f-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="9e55f-146">如何：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="9e55f-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="9e55f-147">如何：Access services 搭配雙工合約</span><span class="sxs-lookup"><span data-stu-id="9e55f-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="9e55f-148">ServiceModel Metadata Utility 工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9e55f-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="9e55f-149">如何：使用 Svcutil.exe 來下載中繼資料文件</span><span class="sxs-lookup"><span data-stu-id="9e55f-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="9e55f-150">如何：發佈服務，使用組態檔的中繼資料</span><span class="sxs-lookup"><span data-stu-id="9e55f-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9e55f-151">使用繫結設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="9e55f-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9e55f-152">開始使用範例</span><span class="sxs-lookup"><span data-stu-id="9e55f-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="9e55f-153">Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="9e55f-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="9e55f-154">自我裝載</span><span class="sxs-lookup"><span data-stu-id="9e55f-154">Self-Host</span></span>](samples/self-host.md)
