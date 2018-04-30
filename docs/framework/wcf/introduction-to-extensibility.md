---
title: 擴充性簡介
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991c3879990fd5b6562a2270c65e1560efadc022
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="introduction-to-extensibility"></a><span data-ttu-id="c0b51-102">擴充性簡介</span><span class="sxs-lookup"><span data-stu-id="c0b51-102">Introduction to Extensibility</span></span>
<span data-ttu-id="c0b51-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式模型是設計用來解決任何分散式應用程式大部分的通訊要求，</span><span class="sxs-lookup"><span data-stu-id="c0b51-103">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application model is designed to solve the greater part of the communication requirements of any distributed application.</span></span> <span data-ttu-id="c0b51-104">但是一定有預設應用程式模型和系統提供的實作所不支援的情況。</span><span class="sxs-lookup"><span data-stu-id="c0b51-104">But there are always scenarios that the default application model and system-provided implementations do not support.</span></span> <span data-ttu-id="c0b51-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 擴充性模型是用來讓您能修改每個層級的系統行為，甚至到取代整個系統模型，所以可以支援自訂的情況。</span><span class="sxs-lookup"><span data-stu-id="c0b51-105">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] extensibility model is intended to support custom scenarios by enabling you to modify system behavior at every level, even to the point of replacing the entire application model.</span></span> <span data-ttu-id="c0b51-106">本主題會概述各種擴充區域，並指向每個擴充區域的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c0b51-106">This topic outlines the various areas of extension and points to more information about each.</span></span>  
  
## <a name="areas-to-extend"></a><span data-ttu-id="c0b51-107">要擴充的區域</span><span class="sxs-lookup"><span data-stu-id="c0b51-107">Areas to Extend</span></span>  
 <span data-ttu-id="c0b51-108">您可以擴充：</span><span class="sxs-lookup"><span data-stu-id="c0b51-108">You can extend:</span></span>  
  
-   <span data-ttu-id="c0b51-109">應用程式執行階段，</span><span class="sxs-lookup"><span data-stu-id="c0b51-109">The application runtime.</span></span> <span data-ttu-id="c0b51-110">這會擴充應用程式的訊息分派和處理功能。</span><span class="sxs-lookup"><span data-stu-id="c0b51-110">This extends the dispatching and the processing of messages for the application.</span></span> <span data-ttu-id="c0b51-111">這個區域也包含擴充安全性系統、中繼資料系統、序列化系統，以及連接應用程式與基礎通道系統的繫結和繫結項目。</span><span class="sxs-lookup"><span data-stu-id="c0b51-111">This area also includes extending the security system, the metadata system, the serialization system, and the bindings and binding elements that connect the application with the underlying channel system.</span></span>  
  
-   <span data-ttu-id="c0b51-112">通道和通道執行階段，</span><span class="sxs-lookup"><span data-stu-id="c0b51-112">The channel and channel runtime.</span></span> <span data-ttu-id="c0b51-113">這會擴充在訊息層級上運作的系統，提供通訊協定、傳輸和編碼支援。</span><span class="sxs-lookup"><span data-stu-id="c0b51-113">This extends the system that functions at the message level, providing protocol, transport, and encoding support.</span></span>  
  
-   <span data-ttu-id="c0b51-114">主機執行階段，</span><span class="sxs-lookup"><span data-stu-id="c0b51-114">The host runtime.</span></span> <span data-ttu-id="c0b51-115">這會擴充裝載應用程式定義域與通道和應用程式執行階段之間的關係。</span><span class="sxs-lookup"><span data-stu-id="c0b51-115">This extends the relationship of the hosting application domain to the channel and application runtime.</span></span>  
  
### <a name="extending-the-application-runtime"></a><span data-ttu-id="c0b51-116">擴充應用程式執行階段</span><span class="sxs-lookup"><span data-stu-id="c0b51-116">Extending the Application Runtime</span></span>  
 <span data-ttu-id="c0b51-117">在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式中，用於對應通道的訊息和用於應用程式本身的訊息之間有不同之處。</span><span class="sxs-lookup"><span data-stu-id="c0b51-117">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications, there is a distinction between messages that are destined for a corresponding channel and messages that are destined for the application itself.</span></span> <span data-ttu-id="c0b51-118">通道訊息支援某些與通道相關的功能，例如建立安全對話或建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0b51-118">Channel messages support some channel-related functionality, such as establishing a secure conversation or establishing a reliable session.</span></span> <span data-ttu-id="c0b51-119">這些訊息不適用於應用程式執行階段，在使用應用程式層之前，就會先處理訊息。</span><span class="sxs-lookup"><span data-stu-id="c0b51-119">These messages are not available to the application runtime; they are processed before the application layer is involved.</span></span>  
  
 <span data-ttu-id="c0b51-120">應用程式訊息包含您或您的客戶所建立，並且用於用戶端或服務作業的資料。</span><span class="sxs-lookup"><span data-stu-id="c0b51-120">Application messages contain data that is destined for a client or service operation that you or your customer has created.</span></span> <span data-ttu-id="c0b51-121">視您的需要而定，這些訊息適用於形式為訊息或物件的應用程式層級擴充系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-121">These messages are available to the application-level extension system in message or object form, depending upon your needs.</span></span>  
  
 <span data-ttu-id="c0b51-122">所有訊息都會通過通道系統，但是只有應用程式訊息會從通道系統傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0b51-122">All messages pass through the channel system; only application messages are passed from the channel system into the application.</span></span> <span data-ttu-id="c0b51-123">若要建立新的通道層級功能，您必須擴充通道系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-123">To create new channel-level functionality, you must extend the channel system.</span></span> <span data-ttu-id="c0b51-124">若要建立新的應用程式層級功能，您必須擴充服務或用戶端執行階段 (分別是發送器和通道處理站)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-124">To create new application-level functionality, you must extend the service or client runtime (dispatchers and channel factories, respectively).</span></span> <span data-ttu-id="c0b51-125">如需擴充應用程式執行階段的詳細資訊，請參閱[擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-125">For more information about extending the application runtime, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
#### <a name="extending-security"></a><span data-ttu-id="c0b51-126">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="c0b51-126">Extending Security</span></span>  
 <span data-ttu-id="c0b51-127">若要建置自訂安全性機制，例如權杖和認證，您必須擴充安全性系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-127">To build custom security mechanisms such as tokens and credentials, you must extend the security system.</span></span> <span data-ttu-id="c0b51-128">如需詳細資訊，請參閱[擴充安全性](../../../docs/framework/wcf/extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-128">For more information, see [Extending Security](../../../docs/framework/wcf/extending/extending-security.md).</span></span>  
  
#### <a name="extending-metadata"></a><span data-ttu-id="c0b51-129">擴充中繼資料</span><span class="sxs-lookup"><span data-stu-id="c0b51-129">Extending Metadata</span></span>  
 <span data-ttu-id="c0b51-130">若要以不同於預設的方式公開中繼資料，您必須擴充中繼資料系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-130">To expose your metadata in differently than the default, you must extend the metadata system.</span></span> <span data-ttu-id="c0b51-131">如需詳細資訊，請參閱[擴充中繼資料系統](../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-131">For more information, see [Extending the Metadata System](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
#### <a name="extending-serialization"></a><span data-ttu-id="c0b51-132">擴充序列化</span><span class="sxs-lookup"><span data-stu-id="c0b51-132">Extending Serialization</span></span>  
 <span data-ttu-id="c0b51-133">若要建置自訂編碼器、提供資料代理或其他涉及自訂傳輸資料的工作，您必須擴充序列化系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-133">To build custom encoders, provide data surrogates, or other work involving the customization of transferred data, you must extend the serialization system.</span></span> <span data-ttu-id="c0b51-134">如需詳細資訊，請參閱[擴充編碼器與序列化程式](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-134">For more information, see [Extending Encoders and Serializers](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).</span></span>  
  
#### <a name="extending-bindings"></a><span data-ttu-id="c0b51-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="c0b51-135">Extending Bindings</span></span>  
 <span data-ttu-id="c0b51-136">若要將傳輸或通訊協定通道與應用程式層產生關聯，您必須擴充繫結系統。</span><span class="sxs-lookup"><span data-stu-id="c0b51-136">To associate transport or protocol channels with the application layer, you must extend the binding system.</span></span> <span data-ttu-id="c0b51-137">如需詳細資訊，請參閱[擴充繫結](../../../docs/framework/wcf/extending/extending-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-137">For more information, see [Extending Bindings](../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
### <a name="extending-the-channel-system"></a><span data-ttu-id="c0b51-138">擴充通道系統</span><span class="sxs-lookup"><span data-stu-id="c0b51-138">Extending the Channel System</span></span>  
 <span data-ttu-id="c0b51-139">若要建立通道支援自訂傳輸或通訊協定功能，請參閱[擴充通道層](../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-139">To create channels that support custom transports or protocol functionality, see [Extending the Channel Layer](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).</span></span>  
  
### <a name="extending-the-service-hosting-system"></a><span data-ttu-id="c0b51-140">擴充服務裝載系統</span><span class="sxs-lookup"><span data-stu-id="c0b51-140">Extending the Service Hosting System</span></span>  
 <span data-ttu-id="c0b51-141">若要修改服務範圍的應用程式模型，您必須擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="c0b51-141">To modify the service-wide application model, you must extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c0b51-142">如需詳細資訊，請參閱[擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-142">For more information, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
 <span data-ttu-id="c0b51-143">若要修改裝載應用程式定義域與服務主機之間的關係，您必須擴充 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="c0b51-143">To modify the relationship between the hosting application domain and the service host, you must extend the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c0b51-144">如需詳細資訊，請參閱[擴充裝載使用 ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b51-144">For more information, see [Extending Hosting Using ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b51-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0b51-145">See Also</span></span>  
 [<span data-ttu-id="c0b51-146">擴充 WCF</span><span class="sxs-lookup"><span data-stu-id="c0b51-146">Extending WCF</span></span>](../../../docs/framework/wcf/extending/index.md)
