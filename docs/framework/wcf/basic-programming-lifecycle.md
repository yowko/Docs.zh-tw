---
title: 基本程式設計週期
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320819"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="228b3-102">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="228b3-102">Basic Programming Lifecycle</span></span>
<span data-ttu-id="228b3-103">Windows Communication Foundation （WCF）可讓應用程式進行通訊，不論它們是在同一部電腦、跨網際網路或不同的應用程式平臺上。</span><span class="sxs-lookup"><span data-stu-id="228b3-103">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="228b3-104">本主題概述建立 WCF 應用程式所需的工作。</span><span class="sxs-lookup"><span data-stu-id="228b3-104">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="228b3-105">如需實用的範例應用程式，請參閱[消費者入門教學](getting-started-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="228b3-105">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="228b3-106">基本工作</span><span class="sxs-lookup"><span data-stu-id="228b3-106">The Basic Tasks</span></span>  
 <span data-ttu-id="228b3-107">要執行的基本工作依序為：</span><span class="sxs-lookup"><span data-stu-id="228b3-107">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="228b3-108">定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="228b3-108">Define the service contract.</span></span> <span data-ttu-id="228b3-109">服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。</span><span class="sxs-lookup"><span data-stu-id="228b3-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="228b3-110">如需詳細資訊，請參閱[設計服務合約](designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-110">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="228b3-111">實作合約。</span><span class="sxs-lookup"><span data-stu-id="228b3-111">Implement the contract.</span></span> <span data-ttu-id="228b3-112">若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="228b3-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="228b3-113">如需詳細資訊，請參閱[執行服務合約](implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-113">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="228b3-114">指定端點與其他行為資訊來設定服務。</span><span class="sxs-lookup"><span data-stu-id="228b3-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="228b3-115">如需詳細資訊，請參閱設定[服務](configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-115">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="228b3-116">裝載服務。</span><span class="sxs-lookup"><span data-stu-id="228b3-116">Host the service.</span></span> <span data-ttu-id="228b3-117">如需詳細資訊，請參閱[裝載服務](hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-117">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="228b3-118">建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="228b3-118">Build a client application.</span></span> <span data-ttu-id="228b3-119">如需詳細資訊，請參閱[建立用戶端](building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-119">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="228b3-120">儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。</span><span class="sxs-lookup"><span data-stu-id="228b3-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="228b3-121">例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。</span><span class="sxs-lookup"><span data-stu-id="228b3-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="228b3-122">或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。</span><span class="sxs-lookup"><span data-stu-id="228b3-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="228b3-123">當您熟悉開發服務合約之後，您也可以閱讀擴充性[簡介](introduction-to-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="228b3-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="228b3-124">如果您的服務有問題，請查看[WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)，以查看其他人是否有相同或類似的問題。</span><span class="sxs-lookup"><span data-stu-id="228b3-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228b3-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="228b3-125">See also</span></span>

- [<span data-ttu-id="228b3-126">履行服務合約</span><span class="sxs-lookup"><span data-stu-id="228b3-126">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
