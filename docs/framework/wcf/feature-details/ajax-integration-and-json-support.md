---
title: AJAX 整合與 JSON 支援
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 0b392044db3fbc926bf77ac305ece294880216d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488825"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="f612c-102">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="f612c-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="f612c-103">Windows Communication Foundation (WCF) 支援的 ASP.NET Asynchronous JavaScript and XML (AJAX) 及 JavaScript Object Notation (JSON) 資料格式讓 WCF 服務公開給 AJAX 用戶端的作業。</span><span class="sxs-lookup"><span data-stu-id="f612c-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="f612c-104">AJAX 用戶端是執行 JavaScript 程式碼和存取這些 WCF 服務，使用 HTTP 要求的網頁。</span><span class="sxs-lookup"><span data-stu-id="f612c-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="f612c-105">本節中的主題會提供有關此支援以及如何實作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f612c-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="f612c-106">如需 ASP.NET AJAX 和它與 ASP.NET 2.0 整合，請參閱[ASP.NET AJAX 概觀](http://go.microsoft.com/fwlink/?LinkId=96725)。</span><span class="sxs-lookup"><span data-stu-id="f612c-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f612c-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f612c-107">In This Section</span></span>  
 [<span data-ttu-id="f612c-108">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="f612c-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="f612c-109">描述 WCF 服務如何可以公開給 AJAX 用戶端藉由新增適當的 AJAX 端點，可能是透過組態或使用自訂為產生的服務主機會自動設定 AJAX 端點的服務主機處理站。</span><span class="sxs-lookup"><span data-stu-id="f612c-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="f612c-110">建立不含 ASP.NET 的 WCF AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="f612c-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="f612c-111">描述如何建立 WCF 服務，而不需要使用 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="f612c-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="f612c-112">JSON 和其他資料傳輸格式的支援</span><span class="sxs-lookup"><span data-stu-id="f612c-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="f612c-113">針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。</span><span class="sxs-lookup"><span data-stu-id="f612c-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="f612c-114">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="f612c-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="f612c-115">描述如何將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f612c-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f612c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f612c-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="f612c-117">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="f612c-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
