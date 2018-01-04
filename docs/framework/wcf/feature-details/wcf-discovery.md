---
title: "WCF 探索"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c11daa14a3897b05947dd6f8c3f3be99eb69c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="94a73-102">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="94a73-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="94a73-103"> 支援以使用 WS-Discovery 通訊協定的互通方式，在執行階段能夠找到服務。</span><span class="sxs-lookup"><span data-stu-id="94a73-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="94a73-104"> 服務可以使用多點傳送訊息，向網路公告其可用性，或向探索 Proxy 伺服器公告。</span><span class="sxs-lookup"><span data-stu-id="94a73-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="94a73-105">用戶端應用程式可搜尋網路或探索 Proxy 伺服器，來尋找符合整組準則的服務。</span><span class="sxs-lookup"><span data-stu-id="94a73-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="94a73-106">本節中的主題提供概要並詳細說明此功能的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="94a73-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94a73-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="94a73-107">In This Section</span></span>  
 [<span data-ttu-id="94a73-108">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="94a73-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="94a73-109">提供 WS-Discovery 支援的概要 (由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供)。</span><span class="sxs-lookup"><span data-stu-id="94a73-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="94a73-110">WCF 探索物件模型</span><span class="sxs-lookup"><span data-stu-id="94a73-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="94a73-111">說明物件模型中的類別以及 WS-Discovery 支援的擴充性。</span><span class="sxs-lookup"><span data-stu-id="94a73-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="94a73-112">如何：以程式設計方式將探索能力新增至 WCF 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="94a73-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="94a73-113">示範如何讓 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務呈現可探索狀態。</span><span class="sxs-lookup"><span data-stu-id="94a73-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="94a73-114">實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="94a73-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="94a73-115">說明用來實作探索 Proxy 的必要步驟、使用探索 Proxy 註冊的可探索服務，以及使用探索 Proxy 來尋找服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="94a73-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="94a73-116">探索版本控制</span><span class="sxs-lookup"><span data-stu-id="94a73-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="94a73-117">簡要概述部分新探索功能的原型實作。</span><span class="sxs-lookup"><span data-stu-id="94a73-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="94a73-118">同時也概要說明如何選取要使用的探索版本。</span><span class="sxs-lookup"><span data-stu-id="94a73-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="94a73-119">在組態檔中設定探索</span><span class="sxs-lookup"><span data-stu-id="94a73-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="94a73-120">示範如何設定組態中的探索。</span><span class="sxs-lookup"><span data-stu-id="94a73-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="94a73-121">使用探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="94a73-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="94a73-122">示範如何在寫入 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式時，使用探索用戶端通道。</span><span class="sxs-lookup"><span data-stu-id="94a73-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>
