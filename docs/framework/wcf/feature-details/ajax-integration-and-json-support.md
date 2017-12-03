---
title: "AJAX 整合與 JSON 支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98efc62a133b86ab71e34671bc6385a5a94897ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="35821-102">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="35821-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="35821-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 對 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 及 JavaScript 物件標記法 (JSON) 資料格式的支援，可允許 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務對 AJAX 用戶端公開作業。</span><span class="sxs-lookup"><span data-stu-id="35821-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="35821-104">AJAX 用戶端指的是執行 JavaScript 程式碼並使用 HTTP 要求來存取這些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的網頁。</span><span class="sxs-lookup"><span data-stu-id="35821-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="35821-105">本節中的主題會提供有關此支援以及如何實作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="35821-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="35821-106">ASP.NET AJAX 以及其與整合 ASP.NET 2.0，請參閱[ASP.NET AJAX 概觀](http://go.microsoft.com/fwlink/?LinkId=96725)。</span><span class="sxs-lookup"><span data-stu-id="35821-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35821-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="35821-107">In This Section</span></span>  
 [<span data-ttu-id="35821-108">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="35821-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="35821-109">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何透過組態，或是透過自訂為產生服務主機 (可自動設定 AJAX 端點) 的服務主機處理站來新增適當的 AJAX 端點，以便公開給 AJAX 用戶端。</span><span class="sxs-lookup"><span data-stu-id="35821-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="35821-110">建立不含 ASP.NET 的 WCF AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="35821-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="35821-111">說明如何在不使用 ASP.NET 的情況下，建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="35821-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="35821-112">JSON 和其他資料傳輸格式的支援</span><span class="sxs-lookup"><span data-stu-id="35821-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="35821-113">針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。</span><span class="sxs-lookup"><span data-stu-id="35821-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="35821-114">如何： 將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="35821-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="35821-115">說明如何從啟用 AJAX 的 ASP.NET Web 服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="35821-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35821-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35821-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="35821-117">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="35821-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
