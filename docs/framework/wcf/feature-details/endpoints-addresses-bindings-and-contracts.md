---
title: 端點：位址、繫結和合約
description: 瞭解與 WCF 服務的所有通訊如何透過服務端點進行，讓用戶端存取服務提供的功能。
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247308"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="d63b4-103">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="d63b4-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="d63b4-104">所有與 Windows Communication Foundation （WCF）服務的通訊都是透過服務的*端點*進行。</span><span class="sxs-lookup"><span data-stu-id="d63b4-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="d63b4-105">端點可讓用戶端存取 WCF 服務所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="d63b4-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="d63b4-106">端點包含四項屬性：</span><span class="sxs-lookup"><span data-stu-id="d63b4-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="d63b4-107">指出可在何處找到端點的位址。</span><span class="sxs-lookup"><span data-stu-id="d63b4-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="d63b4-108">指定用戶端可以如何與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="d63b4-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="d63b4-109">識別可用作業的合約。</span><span class="sxs-lookup"><span data-stu-id="d63b4-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="d63b4-110">指定本機端點實作細節的行為集。</span><span class="sxs-lookup"><span data-stu-id="d63b4-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="d63b4-111">本主題討論此端點結構，並說明如何在 WCF 物件模型中表示它。</span><span class="sxs-lookup"><span data-stu-id="d63b4-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="d63b4-112">端點結構</span><span class="sxs-lookup"><span data-stu-id="d63b4-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="d63b4-113">每個端點都包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="d63b4-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="d63b4-114">位址：位址會唯一識別端點並告訴潛在取用者服務的位置。</span><span class="sxs-lookup"><span data-stu-id="d63b4-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="d63b4-115">它在 WCF 物件模型中是由類別表示 <xref:System.ServiceModel.EndpointAddress> 。</span><span class="sxs-lookup"><span data-stu-id="d63b4-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="d63b4-116"><xref:System.ServiceModel.EndpointAddress> 類別包含：</span><span class="sxs-lookup"><span data-stu-id="d63b4-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="d63b4-117"><xref:System.ServiceModel.EndpointAddress.Uri%2A> 屬性，用來代表服務位址。</span><span class="sxs-lookup"><span data-stu-id="d63b4-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="d63b4-118"><xref:System.ServiceModel.EndpointAddress.Identity%2A> 屬性，用來代表服務的安全性身分識別以及一群選用的訊息標頭集合。</span><span class="sxs-lookup"><span data-stu-id="d63b4-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="d63b4-119">選用訊息標頭會用來提供其他更詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="d63b4-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="d63b4-120">如需詳細資訊，請參閱[指定端點位址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="d63b4-121">繫結：繫結會指定與端點的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="d63b4-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="d63b4-122">這包括：</span><span class="sxs-lookup"><span data-stu-id="d63b4-122">This includes:</span></span>

  - <span data-ttu-id="d63b4-123">要使用的傳輸通訊協定 (例如，TCP 或 HTTP)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="d63b4-124">訊息使用的編碼 (例如，文字或二進位)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="d63b4-125">必要的安全性需求 (例如，SSL 或 SOAP 訊息安全性)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="d63b4-126">如需詳細資訊，請參閱 WCF 系結[總覽](../bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="d63b4-127">系結在 WCF 物件模型中是以抽象基類來表示 <xref:System.ServiceModel.Channels.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="d63b4-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="d63b4-128">在大部分情況中，使用者可以使用下列其中一種系統提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="d63b4-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="d63b4-129">如需詳細資訊，請參閱[系統提供的](../system-provided-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="d63b4-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="d63b4-130">合約：合約會概略說明端點公開哪些功能給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d63b4-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="d63b4-131">合約會指定：</span><span class="sxs-lookup"><span data-stu-id="d63b4-131">A contract specifies:</span></span>

  - <span data-ttu-id="d63b4-132">用戶端可以呼叫的作業。</span><span class="sxs-lookup"><span data-stu-id="d63b4-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="d63b4-133">訊息格式。</span><span class="sxs-lookup"><span data-stu-id="d63b4-133">The form of the message.</span></span>

  - <span data-ttu-id="d63b4-134">呼叫作業所需的輸入參數或資料型別。</span><span class="sxs-lookup"><span data-stu-id="d63b4-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="d63b4-135">用戶端可以期待收到的處理或回應訊息型別。</span><span class="sxs-lookup"><span data-stu-id="d63b4-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="d63b4-136">如需定義合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="d63b4-137">行為：您可以使用端點行為來自訂服務端點的本機行為。</span><span class="sxs-lookup"><span data-stu-id="d63b4-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="d63b4-138">端點行為是藉由參與建立 WCF 執行時間的程式來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="d63b4-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="d63b4-139"><xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> 屬性是一個端點行為範例，它可讓您指定不同於 SOAP 或 Web 服務描述語言 (WSDL) 位址的接聽位址。</span><span class="sxs-lookup"><span data-stu-id="d63b4-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="d63b4-140">如需詳細資訊，請參閱[ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="d63b4-141">定義端點</span><span class="sxs-lookup"><span data-stu-id="d63b4-141">Defining Endpoints</span></span>

<span data-ttu-id="d63b4-142">您可以透過命令式程式碼或是宣告式組態來指定服務端點。</span><span class="sxs-lookup"><span data-stu-id="d63b4-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="d63b4-143">如需詳細資訊，請參閱[如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)和[如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="d63b4-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d63b4-144">本節內容</span><span class="sxs-lookup"><span data-stu-id="d63b4-144">In This Section</span></span>

<span data-ttu-id="d63b4-145">本章節說明繫結、端點與位址的用途；說明如何設定繫結與端點；並示範如何使用 `ClientVia` 行為和 `ListenUri` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d63b4-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="d63b4-146">[址](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="d63b4-147">描述如何在 WCF 中定址端點。</span><span class="sxs-lookup"><span data-stu-id="d63b4-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="d63b4-148">[關係](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="d63b4-149">說明如何使用繫結程序來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="d63b4-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="d63b4-150">[協定](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="d63b4-151">說明合約如何定義服務方法。</span><span class="sxs-lookup"><span data-stu-id="d63b4-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="d63b4-152">[如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="d63b4-153">說明如何透過組態建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="d63b4-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="d63b4-154">[如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="d63b4-155">說明如何透過程式碼建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="d63b4-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="d63b4-156">[如何：使用 Svcutil.exe 驗證已編譯的服務程式代碼](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="d63b4-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="d63b4-157">說明如何在不使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)裝載服務的情況下，偵測服務部署和設定中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d63b4-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d63b4-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d63b4-158">See also</span></span>

- [<span data-ttu-id="d63b4-159">設定服務</span><span class="sxs-lookup"><span data-stu-id="d63b4-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="d63b4-160">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="d63b4-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
