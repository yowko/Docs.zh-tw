---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945934"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="2f6b2-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="2f6b2-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="2f6b2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2f6b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f6b2-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="2f6b2-104">ID</span></span>|<span data-ttu-id="2f6b2-105">3552</span><span class="sxs-lookup"><span data-stu-id="2f6b2-105">3552</span></span>|  
|<span data-ttu-id="2f6b2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2f6b2-106">Keywords</span></span>|<span data-ttu-id="2f6b2-107">配額、WFServices</span><span class="sxs-lookup"><span data-stu-id="2f6b2-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="2f6b2-108">層級</span><span class="sxs-lookup"><span data-stu-id="2f6b2-108">Level</span></span>|<span data-ttu-id="2f6b2-109">警告</span><span class="sxs-lookup"><span data-stu-id="2f6b2-109">Warning</span></span>|  
|<span data-ttu-id="2f6b2-110">通道</span><span class="sxs-lookup"><span data-stu-id="2f6b2-110">Channel</span></span>|<span data-ttu-id="2f6b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2f6b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f6b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="2f6b2-112">Description</span></span>  
 <span data-ttu-id="2f6b2-113">表示已達到節流 'MaxPendingMessagesPerChannel' 限制。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f6b2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="2f6b2-114">Message</span></span>  
 <span data-ttu-id="2f6b2-115">已達到節流 'MaxPendingMessagesPerChannel' 限制 '%1'。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="2f6b2-116">若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f6b2-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2f6b2-117">Details</span></span>  
  
|<span data-ttu-id="2f6b2-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2f6b2-118">Data Item Name</span></span>|<span data-ttu-id="2f6b2-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2f6b2-119">Data Item Type</span></span>|<span data-ttu-id="2f6b2-120">描述</span><span class="sxs-lookup"><span data-stu-id="2f6b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f6b2-121">限制</span><span class="sxs-lookup"><span data-stu-id="2f6b2-121">Limit</span></span>|<span data-ttu-id="2f6b2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f6b2-122">xs:string</span></span>|<span data-ttu-id="2f6b2-123">已達到 MaxPendingMessagesPerChannel 節流的限制。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="2f6b2-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2f6b2-124">AppDomain</span></span>|<span data-ttu-id="2f6b2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f6b2-125">xs:string</span></span>|<span data-ttu-id="2f6b2-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
