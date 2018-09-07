---
title: AJAX 整合與 JSON 支援
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: bcf1cab9386d9d9503af6258c1bb39f8744c073b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061243"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="b17e1-102">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="b17e1-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="b17e1-103">Windows Communication Foundation (WCF) 會對 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 及 JavaScript Object Notation (JSON) 資料格式可讓 WCF 服務對 AJAX 用戶端公開作業。</span><span class="sxs-lookup"><span data-stu-id="b17e1-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="b17e1-104">AJAX 用戶端執行的 JavaScript 程式碼並存取這些 WCF 服務，使用 HTTP 要求的網頁。</span><span class="sxs-lookup"><span data-stu-id="b17e1-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="b17e1-105">本節中的主題會提供有關此支援以及如何實作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b17e1-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="b17e1-106">ASP.NET AJAX 的詳細資訊和與 ASP.NET 2.0 整合，請參閱[ASP.NET AJAX 概觀](https://go.microsoft.com/fwlink/?LinkId=96725)。</span><span class="sxs-lookup"><span data-stu-id="b17e1-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b17e1-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b17e1-107">In This Section</span></span>  
 [<span data-ttu-id="b17e1-108">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b17e1-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="b17e1-109">描述如何 WCF 服務可以公開給 AJAX 用戶端藉由新增適當的 AJAX 端點，透過組態或使用自訂為產生的服務主機會自動設定 AJAX 端點的服務主機處理站。</span><span class="sxs-lookup"><span data-stu-id="b17e1-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="b17e1-110">建立不含 ASP.NET 的 WCF AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="b17e1-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="b17e1-111">說明如何不使用 ASP.NET 建立的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b17e1-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="b17e1-112">JSON 和其他資料傳輸格式的支援</span><span class="sxs-lookup"><span data-stu-id="b17e1-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="b17e1-113">針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。</span><span class="sxs-lookup"><span data-stu-id="b17e1-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="b17e1-114">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="b17e1-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="b17e1-115">描述如何將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF Web 服務。</span><span class="sxs-lookup"><span data-stu-id="b17e1-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b17e1-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="b17e1-117">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="b17e1-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
