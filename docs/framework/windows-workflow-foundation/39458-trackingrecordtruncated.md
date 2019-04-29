---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774409"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="1635b-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="1635b-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="1635b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1635b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1635b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="1635b-104">ID</span></span>|<span data-ttu-id="1635b-105">39458</span><span class="sxs-lookup"><span data-stu-id="1635b-105">39458</span></span>|  
|<span data-ttu-id="1635b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1635b-106">Keywords</span></span>|<span data-ttu-id="1635b-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="1635b-107">WFTracking</span></span>|  
|<span data-ttu-id="1635b-108">層級</span><span class="sxs-lookup"><span data-stu-id="1635b-108">Level</span></span>|<span data-ttu-id="1635b-109">警告</span><span class="sxs-lookup"><span data-stu-id="1635b-109">Warning</span></span>|  
|<span data-ttu-id="1635b-110">通道</span><span class="sxs-lookup"><span data-stu-id="1635b-110">Channel</span></span>|<span data-ttu-id="1635b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1635b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1635b-112">描述</span><span class="sxs-lookup"><span data-stu-id="1635b-112">Description</span></span>  
 <span data-ttu-id="1635b-113">表示追蹤記錄已被截斷。</span><span class="sxs-lookup"><span data-stu-id="1635b-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="1635b-114">變數/標註/使用者資料已移除。</span><span class="sxs-lookup"><span data-stu-id="1635b-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1635b-115">訊息</span><span class="sxs-lookup"><span data-stu-id="1635b-115">Message</span></span>  
 <span data-ttu-id="1635b-116">已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="1635b-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="1635b-117">變數/附註/使用者資料已移除</span><span class="sxs-lookup"><span data-stu-id="1635b-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="1635b-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1635b-118">Details</span></span>  
  
|<span data-ttu-id="1635b-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1635b-119">Data Item Name</span></span>|<span data-ttu-id="1635b-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1635b-120">Data Item Type</span></span>|<span data-ttu-id="1635b-121">描述</span><span class="sxs-lookup"><span data-stu-id="1635b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1635b-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="1635b-122">RecordNumber</span></span>|<span data-ttu-id="1635b-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="1635b-123">xs:string</span></span>|<span data-ttu-id="1635b-124">追蹤記錄號碼。</span><span class="sxs-lookup"><span data-stu-id="1635b-124">The tracking record number.</span></span>|  
|<span data-ttu-id="1635b-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="1635b-125">ProviderId</span></span>|<span data-ttu-id="1635b-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="1635b-126">xs:string</span></span>|<span data-ttu-id="1635b-127">ETW 提供者 ID。</span><span class="sxs-lookup"><span data-stu-id="1635b-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="1635b-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1635b-128">AppDomain</span></span>|<span data-ttu-id="1635b-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="1635b-129">xs:string</span></span>|<span data-ttu-id="1635b-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1635b-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
