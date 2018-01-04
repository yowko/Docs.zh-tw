---
title: "WCF Web HTTP 程式設計模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f008cfe874ae9e38a71eb3cf5d6b2ed4e6cbdf7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="1605e-102">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="1605e-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="1605e-103">開發人員可以使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP 程式設計模型，公開 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務作業給非 SOAP 的端點。</span><span class="sxs-lookup"><span data-stu-id="1605e-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="1605e-104">本章節中的主題會詳細檢查這項功能。</span><span class="sxs-lookup"><span data-stu-id="1605e-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1605e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="1605e-105">In This Section</span></span>  
 [<span data-ttu-id="1605e-106">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="1605e-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="1605e-107">提供 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP 程式設計模型的概觀。</span><span class="sxs-lookup"><span data-stu-id="1605e-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="1605e-108">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="1605e-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="1605e-109">討論 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP 程式設計模型及其運作方式。</span><span class="sxs-lookup"><span data-stu-id="1605e-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="1605e-110">如何：建立基本 WCF Web HTTP 服務</span><span class="sxs-lookup"><span data-stu-id="1605e-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="1605e-111">描述如何撰寫公開非 SOAP 端點的基本服務。</span><span class="sxs-lookup"><span data-stu-id="1605e-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="1605e-112">如何：將合約公開給 SOAP 和 Web 用戶端</span><span class="sxs-lookup"><span data-stu-id="1605e-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="1605e-113">描述如何撰寫將相同合約同時公開至 SOAP 與非 SOAP 用戶端的基本服務。</span><span class="sxs-lookup"><span data-stu-id="1605e-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="1605e-114">UriTemplate 與 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="1605e-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="1605e-115">描述如何使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable>控制 URI。</span><span class="sxs-lookup"><span data-stu-id="1605e-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="1605e-116">WCF Web HTTP 服務的快取支援</span><span class="sxs-lookup"><span data-stu-id="1605e-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="1605e-117">說明如何指定 WCF Web HTTP 服務的快取行為。</span><span class="sxs-lookup"><span data-stu-id="1605e-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="1605e-118">WCF Web HTTP 格式化</span><span class="sxs-lookup"><span data-stu-id="1605e-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="1605e-119">說明如何指定 WCF Web HTTP 服務的回應格式。</span><span class="sxs-lookup"><span data-stu-id="1605e-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="1605e-120">WCF Web HTTP 錯誤處理</span><span class="sxs-lookup"><span data-stu-id="1605e-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="1605e-121">說明如何傳回錯誤給 WCF Web 用戶端，包括 HTTP 狀態碼，以及額外的使用者定義錯誤資料。</span><span class="sxs-lookup"><span data-stu-id="1605e-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="1605e-122">從 WCF 服務呼叫 REST 樣式服務</span><span class="sxs-lookup"><span data-stu-id="1605e-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="1605e-123">說明如何從 WCF 服務內呼叫 REST 樣式服務。</span><span class="sxs-lookup"><span data-stu-id="1605e-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
