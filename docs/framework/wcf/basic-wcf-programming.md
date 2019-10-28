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
ms.openlocfilehash: eff565fa18e3360170584395adcf2a3e7029ac07
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960924"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="23874-102">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="23874-102">Basic WCF programming</span></span>

<span data-ttu-id="23874-103">本節提供建立 Windows Communication Foundation （WCF）應用程式的基本概念。</span><span class="sxs-lookup"><span data-stu-id="23874-103">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="23874-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="23874-104">In this section</span></span>

 <span data-ttu-id="23874-105">[基本程式設計生命週期](basic-programming-lifecycle.md)</span><span class="sxs-lookup"><span data-stu-id="23874-105">[Basic Programming Lifecycle](basic-programming-lifecycle.md)</span></span>\
 <span data-ttu-id="23874-106">描述設計、建立和部署 WCF 服務和用戶端應用程式的生命週期。</span><span class="sxs-lookup"><span data-stu-id="23874-106">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>

 <span data-ttu-id="23874-107">[設計與實作服務](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="23874-107">[Designing and Implementing Services](designing-and-implementing-services.md)</span></span>\
 <span data-ttu-id="23874-108">說明如何設計和實作服務合約、選擇訊息交換模式、指定錯誤合約，以及其他服務的基本部分。</span><span class="sxs-lookup"><span data-stu-id="23874-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>

 <span data-ttu-id="23874-109">[Configuring Services](configuring-services.md)</span><span class="sxs-lookup"><span data-stu-id="23874-109">[Configuring Services](configuring-services.md)</span></span>\
 <span data-ttu-id="23874-110">描述如何設定 WCF 服務以支援合約需求、自訂本機執行時間行為，以及指示發行服務的位址。</span><span class="sxs-lookup"><span data-stu-id="23874-110">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>

 <span data-ttu-id="23874-111">[主控服務](hosting-services.md)</span><span class="sxs-lookup"><span data-stu-id="23874-111">[Hosting Services](hosting-services.md)</span></span>\
 <span data-ttu-id="23874-112">說明在應用程式中裝載服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="23874-112">Describes the basics of hosting services in an application.</span></span>

 <span data-ttu-id="23874-113">[建置用戶端](building-clients.md)</span><span class="sxs-lookup"><span data-stu-id="23874-113">[Building Clients](building-clients.md)</span></span>\
 <span data-ttu-id="23874-114">描述如何從服務取得中繼資料、將其轉換成 WCF 用戶端程式代碼、處理安全性問題，以及建立、設定和裝載 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="23874-114">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host a WCF client.</span></span>

 <span data-ttu-id="23874-115">擴充性\[簡介](introduction-to-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="23874-115">[Introduction to Extensibility](introduction-to-extensibility.md)\</span></span>
 <span data-ttu-id="23874-116">說明如何擴充 WCF 來建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="23874-116">Describes how to extend WCF to create custom solutions.</span></span>

 <span data-ttu-id="23874-117">[WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)</span><span class="sxs-lookup"><span data-stu-id="23874-117">[WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md)</span></span>\
 <span data-ttu-id="23874-118">說明某些最常發生的問題、解決這些問題的方法，以及如何尋找更多相關問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="23874-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>

 <span data-ttu-id="23874-119">[WCF 和 ASP.NET Web API](wcf-and-aspnet-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="23874-119">[WCF and ASP.NET Web API](wcf-and-aspnet-web-api.md)</span></span>\
 <span data-ttu-id="23874-120">討論這兩項技術、彼此的關聯性和使用時機。</span><span class="sxs-lookup"><span data-stu-id="23874-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>

## <a name="reference"></a><span data-ttu-id="23874-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="23874-121">Reference</span></span>

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Description>

## <a name="related-sections"></a><span data-ttu-id="23874-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="23874-122">Related sections</span></span>

- [<span data-ttu-id="23874-123">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="23874-123">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="23874-124">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="23874-124">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="23874-125">方針及最佳做法</span><span class="sxs-lookup"><span data-stu-id="23874-125">Guidelines and Best Practices</span></span>](guidelines-and-best-practices.md)
- [<span data-ttu-id="23874-126">Windows Communication Foundation 工具</span><span class="sxs-lookup"><span data-stu-id="23874-126">Windows Communication Foundation Tools</span></span>](tools.md)
- [<span data-ttu-id="23874-127">Windows Communication Foundation （WCF）範例</span><span class="sxs-lookup"><span data-stu-id="23874-127">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="23874-128">使用者入門</span><span class="sxs-lookup"><span data-stu-id="23874-128">Getting Started</span></span>](./samples/getting-started-sample.md)
- [<span data-ttu-id="23874-129">使用內嵌程式碼的 IIS 裝載</span><span class="sxs-lookup"><span data-stu-id="23874-129">IIS Hosting Using Inline Code</span></span>](./samples/iis-hosting-using-inline-code.md)
- [<span data-ttu-id="23874-130">自我裝載</span><span class="sxs-lookup"><span data-stu-id="23874-130">Self-Host</span></span>](./samples/self-host.md)
