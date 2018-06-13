---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510649"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="8870f-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8870f-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8870f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8870f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8870f-104">ID</span><span class="sxs-lookup"><span data-stu-id="8870f-104">ID</span></span>|<span data-ttu-id="8870f-105">1018</span><span class="sxs-lookup"><span data-stu-id="8870f-105">1018</span></span>|  
|<span data-ttu-id="8870f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8870f-106">Keywords</span></span>|<span data-ttu-id="8870f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8870f-107">WFRuntime</span></span>|  
|<span data-ttu-id="8870f-108">層級</span><span class="sxs-lookup"><span data-stu-id="8870f-108">Level</span></span>|<span data-ttu-id="8870f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8870f-109">Verbose</span></span>|  
|<span data-ttu-id="8870f-110">通道</span><span class="sxs-lookup"><span data-stu-id="8870f-110">Channel</span></span>|<span data-ttu-id="8870f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8870f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8870f-112">描述</span><span class="sxs-lookup"><span data-stu-id="8870f-112">Description</span></span>  
 <span data-ttu-id="8870f-113">表示 CancelActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="8870f-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8870f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8870f-114">Message</span></span>  
 <span data-ttu-id="8870f-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="8870f-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8870f-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8870f-116">Details</span></span>  
  
|<span data-ttu-id="8870f-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8870f-117">Data Item Name</span></span>|<span data-ttu-id="8870f-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8870f-118">Data Item Type</span></span>|<span data-ttu-id="8870f-119">描述</span><span class="sxs-lookup"><span data-stu-id="8870f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8870f-120">活動</span><span class="sxs-lookup"><span data-stu-id="8870f-120">Activity</span></span>|<span data-ttu-id="8870f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8870f-121">xs:string</span></span>|<span data-ttu-id="8870f-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8870f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8870f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8870f-123">DisplayName</span></span>|<span data-ttu-id="8870f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8870f-124">xs:string</span></span>|<span data-ttu-id="8870f-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8870f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8870f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8870f-126">InstanceId</span></span>|<span data-ttu-id="8870f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8870f-127">xs:string</span></span>|<span data-ttu-id="8870f-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="8870f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8870f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8870f-129">AppDomain</span></span>|<span data-ttu-id="8870f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8870f-130">xs:string</span></span>|<span data-ttu-id="8870f-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8870f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
