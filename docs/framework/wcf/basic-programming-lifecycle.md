---
title: 基本程式設計週期
description: 瞭解建立 WCF 應用程式的工作。 WCF 可讓應用程式在相同電腦上、透過網路，或在不同的應用程式平臺上進行通訊。
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: c672827fff780fd263f5355520bb6ccf02bb902e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245527"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="2e6f3-104">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="2e6f3-104">Basic Programming Lifecycle</span></span>
<span data-ttu-id="2e6f3-105">Windows Communication Foundation （WCF）可讓應用程式進行通訊，不論它們是在同一部電腦、跨網際網路或不同的應用程式平臺上。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="2e6f3-106">本主題概述建立 WCF 應用程式所需的工作。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="2e6f3-107">如需實用的範例應用程式，請參閱[消費者入門教學](getting-started-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="2e6f3-108">基本工作</span><span class="sxs-lookup"><span data-stu-id="2e6f3-108">The Basic Tasks</span></span>  
 <span data-ttu-id="2e6f3-109">要執行的基本工作依序為：</span><span class="sxs-lookup"><span data-stu-id="2e6f3-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="2e6f3-110">定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-110">Define the service contract.</span></span> <span data-ttu-id="2e6f3-111">服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="2e6f3-112">如需詳細資訊，請參閱[設計服務合約](designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="2e6f3-113">實作合約。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-113">Implement the contract.</span></span> <span data-ttu-id="2e6f3-114">若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="2e6f3-115">如需詳細資訊，請參閱[執行服務合約](implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="2e6f3-116">指定端點與其他行為資訊來設定服務。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="2e6f3-117">如需詳細資訊，請參閱設定[服務](configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="2e6f3-118">裝載服務。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-118">Host the service.</span></span> <span data-ttu-id="2e6f3-119">如需詳細資訊，請參閱[裝載服務](hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="2e6f3-120">建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-120">Build a client application.</span></span> <span data-ttu-id="2e6f3-121">如需詳細資訊，請參閱[建立用戶端](building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="2e6f3-122">儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="2e6f3-123">例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="2e6f3-124">或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="2e6f3-125">當您熟悉開發服務合約之後，您也可以閱讀擴充性[簡介](introduction-to-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="2e6f3-126">如果您的服務有問題，請查看[WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)，以查看其他人是否有相同或類似的問題。</span><span class="sxs-lookup"><span data-stu-id="2e6f3-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6f3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e6f3-127">See also</span></span>

- [<span data-ttu-id="2e6f3-128">履行服務合約</span><span class="sxs-lookup"><span data-stu-id="2e6f3-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
