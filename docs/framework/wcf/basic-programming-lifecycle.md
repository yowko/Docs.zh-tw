---
title: 基本程式設計週期
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: 6d9ea3b877e7c735cf789039b2a6956037372888
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330554"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="346d0-102">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="346d0-102">Basic Programming Lifecycle</span></span>
<span data-ttu-id="346d0-103">Windows Communication Foundation (WCF) 可讓它們是否在相同的電腦上透過網際網路，或在不同的應用程式平台上進行通訊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="346d0-103">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="346d0-104">本主題概述建置 WCF 應用程式所需的工作。</span><span class="sxs-lookup"><span data-stu-id="346d0-104">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="346d0-105">使用範例應用程式，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="346d0-106">基本工作</span><span class="sxs-lookup"><span data-stu-id="346d0-106">The Basic Tasks</span></span>  
 <span data-ttu-id="346d0-107">要執行的基本工作依序為：</span><span class="sxs-lookup"><span data-stu-id="346d0-107">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="346d0-108">定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="346d0-108">Define the service contract.</span></span> <span data-ttu-id="346d0-109">服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。</span><span class="sxs-lookup"><span data-stu-id="346d0-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="346d0-110">如需詳細資訊，請參閱 < [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-110">For more information, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="346d0-111">實作合約。</span><span class="sxs-lookup"><span data-stu-id="346d0-111">Implement the contract.</span></span> <span data-ttu-id="346d0-112">若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="346d0-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="346d0-113">如需詳細資訊，請參閱 < [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-113">For more information, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="346d0-114">指定端點與其他行為資訊來設定服務。</span><span class="sxs-lookup"><span data-stu-id="346d0-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="346d0-115">如需詳細資訊，請參閱 < [Configuring](../../../docs/framework/wcf/configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-115">For more information, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4. <span data-ttu-id="346d0-116">裝載服務。</span><span class="sxs-lookup"><span data-stu-id="346d0-116">Host the service.</span></span> <span data-ttu-id="346d0-117">如需詳細資訊，請參閱 <<c0> [ 裝載的服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-117">For more information, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5. <span data-ttu-id="346d0-118">建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="346d0-118">Build a client application.</span></span> <span data-ttu-id="346d0-119">如需詳細資訊，請參閱 <<c0> [ 建置用戶端](../../../docs/framework/wcf/building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-119">For more information, see [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="346d0-120">儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。</span><span class="sxs-lookup"><span data-stu-id="346d0-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="346d0-121">例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。</span><span class="sxs-lookup"><span data-stu-id="346d0-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="346d0-122">或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。</span><span class="sxs-lookup"><span data-stu-id="346d0-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="346d0-123">一旦您已熟悉開發服務合約，您也可以閱讀[擴充性簡介](../../../docs/framework/wcf/introduction-to-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="346d0-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="346d0-124">如果您有與您的服務的問題，請檢查[WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)若要查看其他人是否有相同或類似的問題。</span><span class="sxs-lookup"><span data-stu-id="346d0-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346d0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="346d0-125">See also</span></span>

- [<span data-ttu-id="346d0-126">實作服務合約</span><span class="sxs-lookup"><span data-stu-id="346d0-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
