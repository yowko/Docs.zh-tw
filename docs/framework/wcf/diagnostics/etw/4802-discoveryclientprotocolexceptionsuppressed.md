---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.date: 03/30/2017
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
ms.openlocfilehash: e840c5d2e28a5240570a11e8edffe963d54b1e2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242613"
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="12ac4-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="12ac4-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>

## <a name="properties"></a><span data-ttu-id="12ac4-103">屬性</span><span class="sxs-lookup"><span data-stu-id="12ac4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12ac4-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="12ac4-104">ID</span></span>|<span data-ttu-id="12ac4-105">4802</span><span class="sxs-lookup"><span data-stu-id="12ac4-105">4802</span></span>|  
|<span data-ttu-id="12ac4-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="12ac4-106">Keywords</span></span>|<span data-ttu-id="12ac4-107">探索</span><span class="sxs-lookup"><span data-stu-id="12ac4-107">Discovery</span></span>|  
|<span data-ttu-id="12ac4-108">層級</span><span class="sxs-lookup"><span data-stu-id="12ac4-108">Level</span></span>|<span data-ttu-id="12ac4-109">資訊</span><span class="sxs-lookup"><span data-stu-id="12ac4-109">Information</span></span>|  
|<span data-ttu-id="12ac4-110">通路</span><span class="sxs-lookup"><span data-stu-id="12ac4-110">Channel</span></span>|<span data-ttu-id="12ac4-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="12ac4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="12ac4-112">描述</span><span class="sxs-lookup"><span data-stu-id="12ac4-112">Description</span></span>  

 <span data-ttu-id="12ac4-113">如果 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="12ac4-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="12ac4-114">訊息</span><span class="sxs-lookup"><span data-stu-id="12ac4-114">Message</span></span>  

 <span data-ttu-id="12ac4-115">ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="12ac4-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="12ac4-116">這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。</span><span class="sxs-lookup"><span data-stu-id="12ac4-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="12ac4-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12ac4-117">Details</span></span>
