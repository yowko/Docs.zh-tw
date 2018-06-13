---
title: 基本 WCF 程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
ms.openlocfilehash: cbdc693197344fe570c1462f6ca3115018eb69d6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803737"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="33c71-102">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="33c71-102">Basic WCF Programming</span></span>
<span data-ttu-id="33c71-103">本節提供建立 Windows Communication Foundation (WCF) 應用程式的基本概念。</span><span class="sxs-lookup"><span data-stu-id="33c71-103">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33c71-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="33c71-104">In This Section</span></span>  
 [<span data-ttu-id="33c71-105">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="33c71-105">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 <span data-ttu-id="33c71-106">說明設計、 建置和部署 WCF 服務和用戶端應用程式的生命週期。</span><span class="sxs-lookup"><span data-stu-id="33c71-106">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>  
  
 [<span data-ttu-id="33c71-107">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="33c71-107">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 <span data-ttu-id="33c71-108">說明如何設計和實作服務合約、選擇訊息交換模式、指定錯誤合約，以及其他服務的基本部分。</span><span class="sxs-lookup"><span data-stu-id="33c71-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>  
  
 [<span data-ttu-id="33c71-109">設定服務</span><span class="sxs-lookup"><span data-stu-id="33c71-109">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 <span data-ttu-id="33c71-110">描述如何設定 WCF 服務以支援合約要求、 自訂本機執行階段行為，以及指示發行服務的位址。</span><span class="sxs-lookup"><span data-stu-id="33c71-110">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>  
  
 [<span data-ttu-id="33c71-111">裝載服務</span><span class="sxs-lookup"><span data-stu-id="33c71-111">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 <span data-ttu-id="33c71-112">說明在應用程式中裝載服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="33c71-112">Describes the basics of hosting services in an application.</span></span>  
  
 [<span data-ttu-id="33c71-113">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="33c71-113">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 <span data-ttu-id="33c71-114">描述如何從服務取得中繼資料、 將其轉換為 WCF 用戶端程式碼、 處理安全性問題，以及建置、 設定和裝載 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="33c71-114">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host an WCF client.</span></span>  
  
 [<span data-ttu-id="33c71-115">擴充性簡介</span><span class="sxs-lookup"><span data-stu-id="33c71-115">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
 <span data-ttu-id="33c71-116">說明如何擴充 WCF 來建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="33c71-116">Describes how to extend WCF to create custom solutions.</span></span>  
  
 [<span data-ttu-id="33c71-117">WCF 疑難排解快速入門</span><span class="sxs-lookup"><span data-stu-id="33c71-117">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 <span data-ttu-id="33c71-118">說明某些最常發生的問題、解決這些問題的方法，以及如何尋找更多相關問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="33c71-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>  
  
 [<span data-ttu-id="33c71-119">WCF 與 ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="33c71-119">WCF and ASP.NET Web API</span></span>](../../../docs/framework/wcf/wcf-and-aspnet-web-api.md)  
 <span data-ttu-id="33c71-120">討論這兩項技術、彼此的關聯性和使用時機。</span><span class="sxs-lookup"><span data-stu-id="33c71-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="33c71-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="33c71-121">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="33c71-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="33c71-122">Related Sections</span></span>  
 [<span data-ttu-id="33c71-123">系統需求</span><span class="sxs-lookup"><span data-stu-id="33c71-123">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)  
  
 [<span data-ttu-id="33c71-124">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="33c71-124">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
  
 [<span data-ttu-id="33c71-125">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="33c71-125">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="33c71-126">方針及最佳做法</span><span class="sxs-lookup"><span data-stu-id="33c71-126">Guidelines and Best Practices</span></span>](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
  
 [<span data-ttu-id="33c71-127">Windows Communication Foundation 工具</span><span class="sxs-lookup"><span data-stu-id="33c71-127">Windows Communication Foundation Tools</span></span>](../../../docs/framework/wcf/tools.md)  
  
 [<span data-ttu-id="33c71-128">Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="33c71-128">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [<span data-ttu-id="33c71-129">快速入門</span><span class="sxs-lookup"><span data-stu-id="33c71-129">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
  
 [<span data-ttu-id="33c71-130">使用內嵌程式碼的 IIS 裝載</span><span class="sxs-lookup"><span data-stu-id="33c71-130">IIS Hosting Using Inline Code</span></span>](../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)  
  
 [<span data-ttu-id="33c71-131">自我裝載</span><span class="sxs-lookup"><span data-stu-id="33c71-131">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
