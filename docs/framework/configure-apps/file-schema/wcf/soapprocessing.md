---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e83bfc0f868526ad5366032f08956a6c14a1056
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="e2475-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="e2475-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="e2475-103">定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="e2475-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="e2475-104">**\<系統。ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="e2475-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="e2475-105">&nbsp;&nbsp;**\<行為 >** </span><span class="sxs-lookup"><span data-stu-id="e2475-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="e2475-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="e2475-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="e2475-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<行為 >** </span><span class="sxs-lookup"><span data-stu-id="e2475-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="e2475-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="e2475-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e2475-109">語法</span><span class="sxs-lookup"><span data-stu-id="e2475-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2475-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e2475-110">Attributes and elements</span></span>

<span data-ttu-id="e2475-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2475-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2475-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e2475-112">Attributes</span></span>

|                   | <span data-ttu-id="e2475-113">說明</span><span class="sxs-lookup"><span data-stu-id="e2475-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="e2475-114">布林值，這個值指定是否應該在 SOAP 訊息版本之間封送處理訊息。</span><span class="sxs-lookup"><span data-stu-id="e2475-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e2475-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e2475-115">Child elements</span></span>

<span data-ttu-id="e2475-116">無</span><span class="sxs-lookup"><span data-stu-id="e2475-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2475-117">父元素</span><span class="sxs-lookup"><span data-stu-id="e2475-117">Parent elements</span></span>

|     | <span data-ttu-id="e2475-118">說明</span><span class="sxs-lookup"><span data-stu-id="e2475-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e2475-119">**\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="e2475-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="e2475-120">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="e2475-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e2475-121">備註</span><span class="sxs-lookup"><span data-stu-id="e2475-121">Remarks</span></span>

<span data-ttu-id="e2475-122">SOAP 處理是在訊息版本之間轉換訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="e2475-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="e2475-123">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 路由服務可以將其中一種通訊協定的訊息轉換為另一種通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e2475-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="e2475-124">如果傳入及傳出的訊息版本不同，會建立正確版本的新訊息。</span><span class="sxs-lookup"><span data-stu-id="e2475-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="e2475-125">處理訊息<!--zz <xref:System.ServiceModel.Channel.MessageVersion> -->`MessageVersion`到另一個透過建構新[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]包含主體部分和相關的標頭從傳入訊息[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]訊息。</span><span class="sxs-lookup"><span data-stu-id="e2475-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="e2475-126">定址專用或是在路由器層級辨識的標頭，不會在建構新 WCF 訊息期間使用，因為這些標頭不是屬於不同的版本 (若為定址標頭)，就是已做為用戶端和路由器之間通訊的一部分處理。</span><span class="sxs-lookup"><span data-stu-id="e2475-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="e2475-127">標頭是否放置在傳出訊息內，是透過標頭是否在通過傳入通道層時標記為辨識所決定。</span><span class="sxs-lookup"><span data-stu-id="e2475-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="e2475-128">未經辨識的標題 (例如自訂標題) 不會被移除，因此會透過複製到傳出訊息中的方式通過路由服務。</span><span class="sxs-lookup"><span data-stu-id="e2475-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="e2475-129">訊息的主體會複製到傳出訊息中。</span><span class="sxs-lookup"><span data-stu-id="e2475-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="e2475-130">接著，會將訊息傳出到輸出通道，此時會建立並加入該通訊協定/傳輸專用的所有標題和其他封套資料。</span><span class="sxs-lookup"><span data-stu-id="e2475-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="e2475-131">此類處理步驟會在指定 SOAP 處理行為時發生。</span><span class="sxs-lookup"><span data-stu-id="e2475-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="e2475-132">這[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)行為是端點行為，路由服務啟動時，會套用至所有的用戶端 （連出） 端點。</span><span class="sxs-lookup"><span data-stu-id="e2475-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="e2475-133">預設值， [\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為會建立並附加新[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)行為`processMessages`設`true`每個用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="e2475-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="e2475-134">如果路由服務無法辨識您的通訊協定，或者您想要覆寫預設的處理行為，可以停用整個路由服務的 SOAP 處理，或者只停用特定端點的 SOAP 處理。</span><span class="sxs-lookup"><span data-stu-id="e2475-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="e2475-135">若要停用整個路由服務在所有端點上的 SOAP 處理，請設定`soapProcessing`屬性[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為`false`。</span><span class="sxs-lookup"><span data-stu-id="e2475-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="e2475-136">若要關閉特定端點的 SOAP 處理，請使用這個行為，並將其 `processMessages` 屬性設定為 `false`，然後將這個屬性附加至某個端點 (您不希望預設處理程式碼在此端點上執行)。</span><span class="sxs-lookup"><span data-stu-id="e2475-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="e2475-137">當[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為設定路由服務，它會略過重新套用端點行為，因為已經存在。</span><span class="sxs-lookup"><span data-stu-id="e2475-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
