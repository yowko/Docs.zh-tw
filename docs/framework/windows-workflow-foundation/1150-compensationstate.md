---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 61613a27c4d4d8fb0b206246fef25ae87def47a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923860"
---
# <a name="1150---compensationstate"></a><span data-ttu-id="25b9b-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="25b9b-102">1150 - CompensationState</span></span>
## <a name="properties"></a><span data-ttu-id="25b9b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="25b9b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25b9b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="25b9b-104">ID</span></span>|<span data-ttu-id="25b9b-105">1150</span><span class="sxs-lookup"><span data-stu-id="25b9b-105">1150</span></span>|  
|<span data-ttu-id="25b9b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="25b9b-106">Keywords</span></span>|<span data-ttu-id="25b9b-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="25b9b-107">WFActivities</span></span>|  
|<span data-ttu-id="25b9b-108">層級</span><span class="sxs-lookup"><span data-stu-id="25b9b-108">Level</span></span>|<span data-ttu-id="25b9b-109">資訊</span><span class="sxs-lookup"><span data-stu-id="25b9b-109">Information</span></span>|  
|<span data-ttu-id="25b9b-110">通道</span><span class="sxs-lookup"><span data-stu-id="25b9b-110">Channel</span></span>|<span data-ttu-id="25b9b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="25b9b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25b9b-112">描述</span><span class="sxs-lookup"><span data-stu-id="25b9b-112">Description</span></span>  
 <span data-ttu-id="25b9b-113">表示 CompensableActivity 中的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="25b9b-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25b9b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="25b9b-114">Message</span></span>  
 <span data-ttu-id="25b9b-115">CompensableActivity '%1' 處於 '%2' 狀態。</span><span class="sxs-lookup"><span data-stu-id="25b9b-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25b9b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25b9b-116">Details</span></span>  
  
|<span data-ttu-id="25b9b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="25b9b-117">Data Item Name</span></span>|<span data-ttu-id="25b9b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="25b9b-118">Data Item Type</span></span>|<span data-ttu-id="25b9b-119">描述</span><span class="sxs-lookup"><span data-stu-id="25b9b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25b9b-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="25b9b-120">DisplayName</span></span>|<span data-ttu-id="25b9b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="25b9b-121">xs:string</span></span>|<span data-ttu-id="25b9b-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="25b9b-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="25b9b-123">狀況</span><span class="sxs-lookup"><span data-stu-id="25b9b-123">State</span></span>|<span data-ttu-id="25b9b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="25b9b-124">xs:string</span></span>|<span data-ttu-id="25b9b-125">補償狀態。</span><span class="sxs-lookup"><span data-stu-id="25b9b-125">The compensation state.</span></span>|  
|<span data-ttu-id="25b9b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25b9b-126">AppDomain</span></span>|<span data-ttu-id="25b9b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="25b9b-127">xs:string</span></span>|<span data-ttu-id="25b9b-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="25b9b-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
