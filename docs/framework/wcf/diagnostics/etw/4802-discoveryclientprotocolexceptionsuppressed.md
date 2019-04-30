---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.date: 03/30/2017
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
ms.openlocfilehash: 5bb7772d668a6b635130c899ada9879c9c1f69a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943087"
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="e95b2-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="e95b2-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="e95b2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e95b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e95b2-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="e95b2-104">ID</span></span>|<span data-ttu-id="e95b2-105">4802</span><span class="sxs-lookup"><span data-stu-id="e95b2-105">4802</span></span>|  
|<span data-ttu-id="e95b2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e95b2-106">Keywords</span></span>|<span data-ttu-id="e95b2-107">探索</span><span class="sxs-lookup"><span data-stu-id="e95b2-107">Discovery</span></span>|  
|<span data-ttu-id="e95b2-108">層級</span><span class="sxs-lookup"><span data-stu-id="e95b2-108">Level</span></span>|<span data-ttu-id="e95b2-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e95b2-109">Information</span></span>|  
|<span data-ttu-id="e95b2-110">通道</span><span class="sxs-lookup"><span data-stu-id="e95b2-110">Channel</span></span>|<span data-ttu-id="e95b2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e95b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e95b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="e95b2-112">Description</span></span>  
 <span data-ttu-id="e95b2-113">如果 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="e95b2-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e95b2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e95b2-114">Message</span></span>  
 <span data-ttu-id="e95b2-115">ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="e95b2-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="e95b2-116">這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。</span><span class="sxs-lookup"><span data-stu-id="e95b2-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e95b2-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e95b2-117">Details</span></span>
