---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261159"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="c1c3f-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="c1c3f-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="c1c3f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c1c3f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1c3f-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c1c3f-104">ID</span></span>|<span data-ttu-id="c1c3f-105">3552</span><span class="sxs-lookup"><span data-stu-id="c1c3f-105">3552</span></span>|  
|<span data-ttu-id="c1c3f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c1c3f-106">Keywords</span></span>|<span data-ttu-id="c1c3f-107">配額、WFServices</span><span class="sxs-lookup"><span data-stu-id="c1c3f-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="c1c3f-108">層級</span><span class="sxs-lookup"><span data-stu-id="c1c3f-108">Level</span></span>|<span data-ttu-id="c1c3f-109">警告</span><span class="sxs-lookup"><span data-stu-id="c1c3f-109">Warning</span></span>|  
|<span data-ttu-id="c1c3f-110">通路</span><span class="sxs-lookup"><span data-stu-id="c1c3f-110">Channel</span></span>|<span data-ttu-id="c1c3f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c1c3f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c1c3f-112">描述</span><span class="sxs-lookup"><span data-stu-id="c1c3f-112">Description</span></span>  

 <span data-ttu-id="c1c3f-113">表示已達到節流 'MaxPendingMessagesPerChannel' 限制。</span><span class="sxs-lookup"><span data-stu-id="c1c3f-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c1c3f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c1c3f-114">Message</span></span>  

 <span data-ttu-id="c1c3f-115">已達到 '%1' 的節流 'MaxPendingMessagesPerChannel' 限制。</span><span class="sxs-lookup"><span data-stu-id="c1c3f-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="c1c3f-116">若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。</span><span class="sxs-lookup"><span data-stu-id="c1c3f-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c1c3f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1c3f-117">Details</span></span>  
  
|<span data-ttu-id="c1c3f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c1c3f-118">Data Item Name</span></span>|<span data-ttu-id="c1c3f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c1c3f-119">Data Item Type</span></span>|<span data-ttu-id="c1c3f-120">描述</span><span class="sxs-lookup"><span data-stu-id="c1c3f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c1c3f-121">限制</span><span class="sxs-lookup"><span data-stu-id="c1c3f-121">Limit</span></span>|<span data-ttu-id="c1c3f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c1c3f-122">xs:string</span></span>|<span data-ttu-id="c1c3f-123">已達到 MaxPendingMessagesPerChannel 節流的限制。</span><span class="sxs-lookup"><span data-stu-id="c1c3f-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="c1c3f-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c1c3f-124">AppDomain</span></span>|<span data-ttu-id="c1c3f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c1c3f-125">xs:string</span></span>|<span data-ttu-id="c1c3f-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c1c3f-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
