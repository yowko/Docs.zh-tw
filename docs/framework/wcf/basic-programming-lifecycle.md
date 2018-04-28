---
title: 基本程式設計週期
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff735a8caf1fbaff636f94eee366b20c33d8f331
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="b8b44-102">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="b8b44-102">Basic Programming Lifecycle</span></span>
<span data-ttu-id="b8b44-103">不管應用程式位於同一部電腦、位於網際網路的個別電腦上，還是位於不同的應用程式平台，[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 都可以讓應用程式彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="b8b44-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="b8b44-104">本主題將概要說明建置 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式需要執行的工作。</span><span class="sxs-lookup"><span data-stu-id="b8b44-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="b8b44-105">可用的範例應用程式，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="b8b44-106">基本工作</span><span class="sxs-lookup"><span data-stu-id="b8b44-106">The Basic Tasks</span></span>  
 <span data-ttu-id="b8b44-107">要執行的基本工作依序為：</span><span class="sxs-lookup"><span data-stu-id="b8b44-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="b8b44-108">定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="b8b44-108">Define the service contract.</span></span> <span data-ttu-id="b8b44-109">服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。</span><span class="sxs-lookup"><span data-stu-id="b8b44-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="b8b44-110">如需詳細資訊，請參閱[設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-110">For more information, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="b8b44-111">實作合約。</span><span class="sxs-lookup"><span data-stu-id="b8b44-111">Implement the contract.</span></span> <span data-ttu-id="b8b44-112">若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="b8b44-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="b8b44-113">如需詳細資訊，請參閱[實作服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-113">For more information, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="b8b44-114">指定端點與其他行為資訊來設定服務。</span><span class="sxs-lookup"><span data-stu-id="b8b44-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="b8b44-115">如需詳細資訊，請參閱[設定 Services](../../../docs/framework/wcf/configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-115">For more information, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="b8b44-116">裝載服務。</span><span class="sxs-lookup"><span data-stu-id="b8b44-116">Host the service.</span></span> <span data-ttu-id="b8b44-117">如需詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-117">For more information, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="b8b44-118">建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8b44-118">Build a client application.</span></span> <span data-ttu-id="b8b44-119">如需詳細資訊，請參閱[建置用戶端](../../../docs/framework/wcf/building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-119">For more information, see [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="b8b44-120">儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。</span><span class="sxs-lookup"><span data-stu-id="b8b44-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="b8b44-121">例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。</span><span class="sxs-lookup"><span data-stu-id="b8b44-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="b8b44-122">或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。</span><span class="sxs-lookup"><span data-stu-id="b8b44-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="b8b44-123">一旦您熟悉開發服務合約時，您也可以讀取[擴充性簡介](../../../docs/framework/wcf/introduction-to-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b44-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="b8b44-124">如果您有與服務的問題，請檢查[WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)若要查看其他人是否具有相同或類似的問題。</span><span class="sxs-lookup"><span data-stu-id="b8b44-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b44-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8b44-125">See Also</span></span>  
 [<span data-ttu-id="b8b44-126">履行服務合約</span><span class="sxs-lookup"><span data-stu-id="b8b44-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
