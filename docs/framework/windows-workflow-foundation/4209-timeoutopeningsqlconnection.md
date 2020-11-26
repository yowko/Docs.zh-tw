---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9aa8cdffebb0cdf8b1e8225a394edf78ecf032b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238674"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="81a88-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="81a88-102">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="81a88-103">屬性</span><span class="sxs-lookup"><span data-stu-id="81a88-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81a88-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="81a88-104">ID</span></span>|<span data-ttu-id="81a88-105">4209</span><span class="sxs-lookup"><span data-stu-id="81a88-105">4209</span></span>|  
|<span data-ttu-id="81a88-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="81a88-106">Keywords</span></span>|<span data-ttu-id="81a88-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="81a88-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="81a88-108">層級</span><span class="sxs-lookup"><span data-stu-id="81a88-108">Level</span></span>|<span data-ttu-id="81a88-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="81a88-109">Error</span></span>|  
|<span data-ttu-id="81a88-110">通路</span><span class="sxs-lookup"><span data-stu-id="81a88-110">Channel</span></span>|<span data-ttu-id="81a88-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="81a88-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="81a88-112">描述</span><span class="sxs-lookup"><span data-stu-id="81a88-112">Description</span></span>  

 <span data-ttu-id="81a88-113">表示嘗試開啟 SQL 連接時，發生逾時。</span><span class="sxs-lookup"><span data-stu-id="81a88-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="81a88-114">訊息</span><span class="sxs-lookup"><span data-stu-id="81a88-114">Message</span></span>  

 <span data-ttu-id="81a88-115">嘗試開啟 SQL 連接時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="81a88-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="81a88-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="81a88-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="81a88-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="81a88-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="81a88-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="81a88-118">Details</span></span>  
  
|<span data-ttu-id="81a88-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="81a88-119">Data Item Name</span></span>|<span data-ttu-id="81a88-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="81a88-120">Data Item Type</span></span>|<span data-ttu-id="81a88-121">描述</span><span class="sxs-lookup"><span data-stu-id="81a88-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="81a88-122">逾時</span><span class="sxs-lookup"><span data-stu-id="81a88-122">Timeout</span></span>|<span data-ttu-id="81a88-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="81a88-123">xs:string</span></span>|<span data-ttu-id="81a88-124">開啟 SQL 連接的逾時值。</span><span class="sxs-lookup"><span data-stu-id="81a88-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="81a88-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="81a88-125">AppDomain</span></span>|<span data-ttu-id="81a88-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="81a88-126">xs:string</span></span>|<span data-ttu-id="81a88-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="81a88-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
