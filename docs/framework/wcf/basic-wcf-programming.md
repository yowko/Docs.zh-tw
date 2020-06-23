---
title: 基本 WCF 程式設計
description: 如要進行疑難排解，請參閱這些文章以開發 Windows Communication Foundation 應用程式。
ms.date: 03/30/2017
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
ms.openlocfilehash: 6f4de39494902dcffcb25f75a6ff9f57b28547ff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245514"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="01af7-103">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="01af7-103">Basic WCF programming</span></span>

<span data-ttu-id="01af7-104">本節提供建立 Windows Communication Foundation （WCF）應用程式的基本概念。</span><span class="sxs-lookup"><span data-stu-id="01af7-104">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="01af7-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="01af7-105">In this section</span></span>

 <span data-ttu-id="01af7-106">[基本程式設計週期](basic-programming-lifecycle.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-106">[Basic Programming Lifecycle](basic-programming-lifecycle.md)</span></span>\
 <span data-ttu-id="01af7-107">描述設計、建立和部署 WCF 服務和用戶端應用程式的生命週期。</span><span class="sxs-lookup"><span data-stu-id="01af7-107">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>

 <span data-ttu-id="01af7-108">[設計和執行服務](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-108">[Designing and Implementing Services](designing-and-implementing-services.md)</span></span>\
 <span data-ttu-id="01af7-109">說明如何設計和實作服務合約、選擇訊息交換模式、指定錯誤合約，以及其他服務的基本部分。</span><span class="sxs-lookup"><span data-stu-id="01af7-109">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>

 <span data-ttu-id="01af7-110">[設定服務](configuring-services.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-110">[Configuring Services](configuring-services.md)</span></span>\
 <span data-ttu-id="01af7-111">描述如何設定 WCF 服務以支援合約需求、自訂本機執行時間行為，以及指示發行服務的位址。</span><span class="sxs-lookup"><span data-stu-id="01af7-111">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>

 <span data-ttu-id="01af7-112">[裝載服務](hosting-services.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-112">[Hosting Services](hosting-services.md)</span></span>\
 <span data-ttu-id="01af7-113">說明在應用程式中裝載服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="01af7-113">Describes the basics of hosting services in an application.</span></span>

 <span data-ttu-id="01af7-114">[建立用戶端](building-clients.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-114">[Building Clients](building-clients.md)</span></span>\
 <span data-ttu-id="01af7-115">描述如何從服務取得中繼資料、將其轉換成 WCF 用戶端程式代碼、處理安全性問題，以及建立、設定和裝載 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="01af7-115">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host a WCF client.</span></span>

 <span data-ttu-id="01af7-116">[擴充性簡介](introduction-to-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-116">[Introduction to Extensibility](introduction-to-extensibility.md)</span></span>\
 <span data-ttu-id="01af7-117">說明如何擴充 WCF 來建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="01af7-117">Describes how to extend WCF to create custom solutions.</span></span>

 <span data-ttu-id="01af7-118">[WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-118">[WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md)</span></span>\
 <span data-ttu-id="01af7-119">說明某些最常發生的問題、解決這些問題的方法，以及如何尋找更多相關問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="01af7-119">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>

 <span data-ttu-id="01af7-120">[WCF 和 ASP.NET Web API](wcf-and-aspnet-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-120">[WCF and ASP.NET Web API](wcf-and-aspnet-web-api.md)</span></span>\
 <span data-ttu-id="01af7-121">討論這兩項技術、彼此的關聯性和使用時機。</span><span class="sxs-lookup"><span data-stu-id="01af7-121">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>

## <a name="reference"></a><span data-ttu-id="01af7-122">參考</span><span class="sxs-lookup"><span data-stu-id="01af7-122">Reference</span></span>

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Description>

## <a name="related-sections"></a><span data-ttu-id="01af7-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="01af7-123">Related sections</span></span>

- [<span data-ttu-id="01af7-124">概念總覽</span><span class="sxs-lookup"><span data-stu-id="01af7-124">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="01af7-125">消費者入門教學課程</span><span class="sxs-lookup"><span data-stu-id="01af7-125">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="01af7-126">方針及最佳做法</span><span class="sxs-lookup"><span data-stu-id="01af7-126">Guidelines and Best Practices</span></span>](guidelines-and-best-practices.md)
- [<span data-ttu-id="01af7-127">Windows Communication Foundation 工具</span><span class="sxs-lookup"><span data-stu-id="01af7-127">Windows Communication Foundation Tools</span></span>](tools.md)
- [<span data-ttu-id="01af7-128">Windows Communication Foundation (WCF) 範例</span><span class="sxs-lookup"><span data-stu-id="01af7-128">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="01af7-129">快速入門</span><span class="sxs-lookup"><span data-stu-id="01af7-129">Getting Started</span></span>](./samples/getting-started-sample.md)
- [<span data-ttu-id="01af7-130">使用內嵌程式碼的 IIS 裝載</span><span class="sxs-lookup"><span data-stu-id="01af7-130">IIS Hosting Using Inline Code</span></span>](./samples/iis-hosting-using-inline-code.md)
- [<span data-ttu-id="01af7-131">自我裝載</span><span class="sxs-lookup"><span data-stu-id="01af7-131">Self-Host</span></span>](./samples/self-host.md)
