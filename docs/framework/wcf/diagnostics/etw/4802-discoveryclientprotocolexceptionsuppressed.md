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
ms.workload: dotnet
ms.openlocfilehash: ecb147e35b830322240f69f533de7a588064e9d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="81f29-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="81f29-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="81f29-103">屬性</span><span class="sxs-lookup"><span data-stu-id="81f29-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81f29-104">ID</span><span class="sxs-lookup"><span data-stu-id="81f29-104">ID</span></span>|<span data-ttu-id="81f29-105">4802</span><span class="sxs-lookup"><span data-stu-id="81f29-105">4802</span></span>|  
|<span data-ttu-id="81f29-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="81f29-106">Keywords</span></span>|<span data-ttu-id="81f29-107">探索</span><span class="sxs-lookup"><span data-stu-id="81f29-107">Discovery</span></span>|  
|<span data-ttu-id="81f29-108">層級</span><span class="sxs-lookup"><span data-stu-id="81f29-108">Level</span></span>|<span data-ttu-id="81f29-109">資訊</span><span class="sxs-lookup"><span data-stu-id="81f29-109">Information</span></span>|  
|<span data-ttu-id="81f29-110">通道</span><span class="sxs-lookup"><span data-stu-id="81f29-110">Channel</span></span>|<span data-ttu-id="81f29-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="81f29-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="81f29-112">描述</span><span class="sxs-lookup"><span data-stu-id="81f29-112">Description</span></span>  
 <span data-ttu-id="81f29-113">如果 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="81f29-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="81f29-114">訊息</span><span class="sxs-lookup"><span data-stu-id="81f29-114">Message</span></span>  
 <span data-ttu-id="81f29-115">ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="81f29-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="81f29-116">這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。</span><span class="sxs-lookup"><span data-stu-id="81f29-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="81f29-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="81f29-117">Details</span></span>
