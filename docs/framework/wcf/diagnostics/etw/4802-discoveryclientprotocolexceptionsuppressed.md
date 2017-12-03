---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f2b5832b93db61ac42834569c5269e7a6933cc2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="b5044-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="b5044-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="b5044-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b5044-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5044-104">ID</span><span class="sxs-lookup"><span data-stu-id="b5044-104">ID</span></span>|<span data-ttu-id="b5044-105">4802</span><span class="sxs-lookup"><span data-stu-id="b5044-105">4802</span></span>|  
|<span data-ttu-id="b5044-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b5044-106">Keywords</span></span>|<span data-ttu-id="b5044-107">探索</span><span class="sxs-lookup"><span data-stu-id="b5044-107">Discovery</span></span>|  
|<span data-ttu-id="b5044-108">層級</span><span class="sxs-lookup"><span data-stu-id="b5044-108">Level</span></span>|<span data-ttu-id="b5044-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b5044-109">Information</span></span>|  
|<span data-ttu-id="b5044-110">通道</span><span class="sxs-lookup"><span data-stu-id="b5044-110">Channel</span></span>|<span data-ttu-id="b5044-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b5044-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5044-112">描述</span><span class="sxs-lookup"><span data-stu-id="b5044-112">Description</span></span>  
 <span data-ttu-id="b5044-113">如果 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="b5044-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5044-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b5044-114">Message</span></span>  
 <span data-ttu-id="b5044-115">ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="b5044-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="b5044-116">這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。</span><span class="sxs-lookup"><span data-stu-id="b5044-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5044-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b5044-117">Details</span></span>
