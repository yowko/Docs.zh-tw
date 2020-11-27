---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: cb5671ce7a30a7096104ba0ca6c4f36bed6b93f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275228"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="25826-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="25826-102">1027 - StartTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="25826-103">屬性</span><span class="sxs-lookup"><span data-stu-id="25826-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25826-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="25826-104">ID</span></span>|<span data-ttu-id="25826-105">1027</span><span class="sxs-lookup"><span data-stu-id="25826-105">1027</span></span>|  
|<span data-ttu-id="25826-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="25826-106">Keywords</span></span>|<span data-ttu-id="25826-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="25826-107">WFRuntime</span></span>|  
|<span data-ttu-id="25826-108">層級</span><span class="sxs-lookup"><span data-stu-id="25826-108">Level</span></span>|<span data-ttu-id="25826-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="25826-109">Verbose</span></span>|  
|<span data-ttu-id="25826-110">通路</span><span class="sxs-lookup"><span data-stu-id="25826-110">Channel</span></span>|<span data-ttu-id="25826-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="25826-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25826-112">描述</span><span class="sxs-lookup"><span data-stu-id="25826-112">Description</span></span>  

 <span data-ttu-id="25826-113">表示 TransactionContextWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="25826-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25826-114">訊息</span><span class="sxs-lookup"><span data-stu-id="25826-114">Message</span></span>  

 <span data-ttu-id="25826-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="25826-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25826-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25826-116">Details</span></span>  
  
|<span data-ttu-id="25826-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="25826-117">Data Item Name</span></span>|<span data-ttu-id="25826-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="25826-118">Data Item Type</span></span>|<span data-ttu-id="25826-119">描述</span><span class="sxs-lookup"><span data-stu-id="25826-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25826-120">活動</span><span class="sxs-lookup"><span data-stu-id="25826-120">Activity</span></span>|<span data-ttu-id="25826-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="25826-121">xs:string</span></span>|<span data-ttu-id="25826-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="25826-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="25826-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="25826-123">DisplayName</span></span>|<span data-ttu-id="25826-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="25826-124">xs:string</span></span>|<span data-ttu-id="25826-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="25826-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="25826-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="25826-126">InstanceId</span></span>|<span data-ttu-id="25826-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="25826-127">xs:string</span></span>|<span data-ttu-id="25826-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="25826-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="25826-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25826-129">AppDomain</span></span>|<span data-ttu-id="25826-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="25826-130">xs:string</span></span>|<span data-ttu-id="25826-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="25826-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
