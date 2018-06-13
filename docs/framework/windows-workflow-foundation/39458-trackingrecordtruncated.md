---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514478"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="6b522-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="6b522-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="6b522-103">屬性</span><span class="sxs-lookup"><span data-stu-id="6b522-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b522-104">ID</span><span class="sxs-lookup"><span data-stu-id="6b522-104">ID</span></span>|<span data-ttu-id="6b522-105">39458</span><span class="sxs-lookup"><span data-stu-id="6b522-105">39458</span></span>|  
|<span data-ttu-id="6b522-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="6b522-106">Keywords</span></span>|<span data-ttu-id="6b522-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="6b522-107">WFTracking</span></span>|  
|<span data-ttu-id="6b522-108">層級</span><span class="sxs-lookup"><span data-stu-id="6b522-108">Level</span></span>|<span data-ttu-id="6b522-109">警告</span><span class="sxs-lookup"><span data-stu-id="6b522-109">Warning</span></span>|  
|<span data-ttu-id="6b522-110">通道</span><span class="sxs-lookup"><span data-stu-id="6b522-110">Channel</span></span>|<span data-ttu-id="6b522-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6b522-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b522-112">描述</span><span class="sxs-lookup"><span data-stu-id="6b522-112">Description</span></span>  
 <span data-ttu-id="6b522-113">表示追蹤記錄已被截斷。</span><span class="sxs-lookup"><span data-stu-id="6b522-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="6b522-114">變數/標註/使用者資料已移除。</span><span class="sxs-lookup"><span data-stu-id="6b522-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b522-115">訊息</span><span class="sxs-lookup"><span data-stu-id="6b522-115">Message</span></span>  
 <span data-ttu-id="6b522-116">已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6b522-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="6b522-117">變數/附註/使用者資料已移除</span><span class="sxs-lookup"><span data-stu-id="6b522-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b522-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6b522-118">Details</span></span>  
  
|<span data-ttu-id="6b522-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="6b522-119">Data Item Name</span></span>|<span data-ttu-id="6b522-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="6b522-120">Data Item Type</span></span>|<span data-ttu-id="6b522-121">描述</span><span class="sxs-lookup"><span data-stu-id="6b522-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b522-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="6b522-122">RecordNumber</span></span>|<span data-ttu-id="6b522-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="6b522-123">xs:string</span></span>|<span data-ttu-id="6b522-124">追蹤記錄號碼。</span><span class="sxs-lookup"><span data-stu-id="6b522-124">The tracking record number.</span></span>|  
|<span data-ttu-id="6b522-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="6b522-125">ProviderId</span></span>|<span data-ttu-id="6b522-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="6b522-126">xs:string</span></span>|<span data-ttu-id="6b522-127">ETW 提供者 ID。</span><span class="sxs-lookup"><span data-stu-id="6b522-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="6b522-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6b522-128">AppDomain</span></span>|<span data-ttu-id="6b522-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="6b522-129">xs:string</span></span>|<span data-ttu-id="6b522-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="6b522-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
