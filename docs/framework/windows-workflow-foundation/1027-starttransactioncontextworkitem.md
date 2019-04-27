---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008820"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="f01f6-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="f01f6-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f01f6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f01f6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f01f6-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f01f6-104">ID</span></span>|<span data-ttu-id="f01f6-105">1027</span><span class="sxs-lookup"><span data-stu-id="f01f6-105">1027</span></span>|  
|<span data-ttu-id="f01f6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f01f6-106">Keywords</span></span>|<span data-ttu-id="f01f6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f01f6-107">WFRuntime</span></span>|  
|<span data-ttu-id="f01f6-108">層級</span><span class="sxs-lookup"><span data-stu-id="f01f6-108">Level</span></span>|<span data-ttu-id="f01f6-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f01f6-109">Verbose</span></span>|  
|<span data-ttu-id="f01f6-110">通道</span><span class="sxs-lookup"><span data-stu-id="f01f6-110">Channel</span></span>|<span data-ttu-id="f01f6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f01f6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f01f6-112">描述</span><span class="sxs-lookup"><span data-stu-id="f01f6-112">Description</span></span>  
 <span data-ttu-id="f01f6-113">表示 TransactionContextWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="f01f6-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f01f6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f01f6-114">Message</span></span>  
 <span data-ttu-id="f01f6-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f01f6-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f01f6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f01f6-116">Details</span></span>  
  
|<span data-ttu-id="f01f6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f01f6-117">Data Item Name</span></span>|<span data-ttu-id="f01f6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f01f6-118">Data Item Type</span></span>|<span data-ttu-id="f01f6-119">描述</span><span class="sxs-lookup"><span data-stu-id="f01f6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f01f6-120">活動</span><span class="sxs-lookup"><span data-stu-id="f01f6-120">Activity</span></span>|<span data-ttu-id="f01f6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f01f6-121">xs:string</span></span>|<span data-ttu-id="f01f6-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f01f6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f01f6-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f01f6-123">DisplayName</span></span>|<span data-ttu-id="f01f6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f01f6-124">xs:string</span></span>|<span data-ttu-id="f01f6-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f01f6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f01f6-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f01f6-126">InstanceId</span></span>|<span data-ttu-id="f01f6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f01f6-127">xs:string</span></span>|<span data-ttu-id="f01f6-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f01f6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f01f6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f01f6-129">AppDomain</span></span>|<span data-ttu-id="f01f6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f01f6-130">xs:string</span></span>|<span data-ttu-id="f01f6-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f01f6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
