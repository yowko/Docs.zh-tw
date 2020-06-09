---
title: 端點：位址、繫結和合約
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593512"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="effb6-102">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="effb6-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="effb6-103">所有與 Windows Communication Foundation （WCF）服務的通訊都是透過服務的*端點*進行。</span><span class="sxs-lookup"><span data-stu-id="effb6-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="effb6-104">端點可讓用戶端存取 WCF 服務所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="effb6-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="effb6-105">端點包含四項屬性：</span><span class="sxs-lookup"><span data-stu-id="effb6-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="effb6-106">指出可在何處找到端點的位址。</span><span class="sxs-lookup"><span data-stu-id="effb6-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="effb6-107">指定用戶端可以如何與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="effb6-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="effb6-108">識別可用作業的合約。</span><span class="sxs-lookup"><span data-stu-id="effb6-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="effb6-109">指定本機端點實作細節的行為集。</span><span class="sxs-lookup"><span data-stu-id="effb6-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="effb6-110">本主題討論此端點結構，並說明如何在 WCF 物件模型中表示它。</span><span class="sxs-lookup"><span data-stu-id="effb6-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="effb6-111">端點結構</span><span class="sxs-lookup"><span data-stu-id="effb6-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="effb6-112">每個端點都包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="effb6-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="effb6-113">位址：位址會唯一識別端點並告訴潛在取用者服務的位置。</span><span class="sxs-lookup"><span data-stu-id="effb6-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="effb6-114">它在 WCF 物件模型中是由類別表示 <xref:System.ServiceModel.EndpointAddress> 。</span><span class="sxs-lookup"><span data-stu-id="effb6-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="effb6-115"><xref:System.ServiceModel.EndpointAddress> 類別包含：</span><span class="sxs-lookup"><span data-stu-id="effb6-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="effb6-116"><xref:System.ServiceModel.EndpointAddress.Uri%2A> 屬性，用來代表服務位址。</span><span class="sxs-lookup"><span data-stu-id="effb6-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="effb6-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> 屬性，用來代表服務的安全性身分識別以及一群選用的訊息標頭集合。</span><span class="sxs-lookup"><span data-stu-id="effb6-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="effb6-118">選用訊息標頭會用來提供其他更詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="effb6-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="effb6-119">如需詳細資訊，請參閱[指定端點位址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="effb6-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="effb6-120">繫結：繫結會指定與端點的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="effb6-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="effb6-121">包括：</span><span class="sxs-lookup"><span data-stu-id="effb6-121">This includes:</span></span>

  - <span data-ttu-id="effb6-122">要使用的傳輸通訊協定 (例如，TCP 或 HTTP)。</span><span class="sxs-lookup"><span data-stu-id="effb6-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="effb6-123">訊息使用的編碼 (例如，文字或二進位)。</span><span class="sxs-lookup"><span data-stu-id="effb6-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="effb6-124">必要的安全性需求 (例如，SSL 或 SOAP 訊息安全性)。</span><span class="sxs-lookup"><span data-stu-id="effb6-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="effb6-125">如需詳細資訊，請參閱 WCF 系結[總覽](../bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="effb6-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="effb6-126">系結在 WCF 物件模型中是以抽象基類來表示 <xref:System.ServiceModel.Channels.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="effb6-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="effb6-127">在大部分情況中，使用者可以使用下列其中一種系統提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="effb6-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="effb6-128">如需詳細資訊，請參閱[系統提供的](../system-provided-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="effb6-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="effb6-129">合約：合約會概略說明端點公開哪些功能給用戶端。</span><span class="sxs-lookup"><span data-stu-id="effb6-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="effb6-130">合約會指定：</span><span class="sxs-lookup"><span data-stu-id="effb6-130">A contract specifies:</span></span>

  - <span data-ttu-id="effb6-131">用戶端可以呼叫的作業。</span><span class="sxs-lookup"><span data-stu-id="effb6-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="effb6-132">訊息格式。</span><span class="sxs-lookup"><span data-stu-id="effb6-132">The form of the message.</span></span>

  - <span data-ttu-id="effb6-133">呼叫作業所需的輸入參數或資料型別。</span><span class="sxs-lookup"><span data-stu-id="effb6-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="effb6-134">用戶端可以期待收到的處理或回應訊息型別。</span><span class="sxs-lookup"><span data-stu-id="effb6-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="effb6-135">如需定義合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="effb6-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="effb6-136">行為：您可以使用端點行為來自訂服務端點的本機行為。</span><span class="sxs-lookup"><span data-stu-id="effb6-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="effb6-137">端點行為是藉由參與建立 WCF 執行時間的程式來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="effb6-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="effb6-138"><xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> 屬性是一個端點行為範例，它可讓您指定不同於 SOAP 或 Web 服務描述語言 (WSDL) 位址的接聽位址。</span><span class="sxs-lookup"><span data-stu-id="effb6-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="effb6-139">如需詳細資訊，請參閱[ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md)。</span><span class="sxs-lookup"><span data-stu-id="effb6-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="effb6-140">定義端點</span><span class="sxs-lookup"><span data-stu-id="effb6-140">Defining Endpoints</span></span>

<span data-ttu-id="effb6-141">您可以透過命令式程式碼或是宣告式組態來指定服務端點。</span><span class="sxs-lookup"><span data-stu-id="effb6-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="effb6-142">如需詳細資訊，請參閱[如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)和[如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="effb6-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="effb6-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="effb6-143">In This Section</span></span>

<span data-ttu-id="effb6-144">本章節說明繫結、端點與位址的用途；說明如何設定繫結與端點；並示範如何使用 `ClientVia` 行為和 `ListenUri` 屬性。</span><span class="sxs-lookup"><span data-stu-id="effb6-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="effb6-145">[址](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="effb6-146">描述如何在 WCF 中定址端點。</span><span class="sxs-lookup"><span data-stu-id="effb6-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="effb6-147">[關係](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="effb6-148">說明如何使用繫結程序來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="effb6-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="effb6-149">[協定](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="effb6-150">說明合約如何定義服務方法。</span><span class="sxs-lookup"><span data-stu-id="effb6-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="effb6-151">[如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="effb6-152">說明如何透過組態建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="effb6-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="effb6-153">[如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="effb6-154">說明如何透過程式碼建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="effb6-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="effb6-155">[如何：使用 Svcutil 來驗證已編譯的服務程式代碼](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="effb6-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="effb6-156">描述如何使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)，在不裝載服務的情況下，偵測服務執行和設定中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="effb6-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="effb6-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="effb6-157">See also</span></span>

- [<span data-ttu-id="effb6-158">設定服務</span><span class="sxs-lookup"><span data-stu-id="effb6-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="effb6-159">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="effb6-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
