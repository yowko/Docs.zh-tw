---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: b9cfceb12d56f93c0f9726849e34f4333f1399ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239636"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="71e41-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="71e41-102">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="71e41-103">屬性</span><span class="sxs-lookup"><span data-stu-id="71e41-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71e41-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="71e41-104">ID</span></span>|<span data-ttu-id="71e41-105">1012</span><span class="sxs-lookup"><span data-stu-id="71e41-105">1012</span></span>|  
|<span data-ttu-id="71e41-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="71e41-106">Keywords</span></span>|<span data-ttu-id="71e41-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="71e41-107">WFRuntime</span></span>|  
|<span data-ttu-id="71e41-108">層級</span><span class="sxs-lookup"><span data-stu-id="71e41-108">Level</span></span>|<span data-ttu-id="71e41-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="71e41-109">Verbose</span></span>|  
|<span data-ttu-id="71e41-110">通路</span><span class="sxs-lookup"><span data-stu-id="71e41-110">Channel</span></span>|<span data-ttu-id="71e41-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="71e41-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="71e41-112">描述</span><span class="sxs-lookup"><span data-stu-id="71e41-112">Description</span></span>  

 <span data-ttu-id="71e41-113">表示 ExecuteActivityWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="71e41-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="71e41-114">訊息</span><span class="sxs-lookup"><span data-stu-id="71e41-114">Message</span></span>  

 <span data-ttu-id="71e41-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="71e41-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="71e41-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="71e41-116">Details</span></span>  
  
|<span data-ttu-id="71e41-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="71e41-117">Data Item Name</span></span>|<span data-ttu-id="71e41-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="71e41-118">Data Item Type</span></span>|<span data-ttu-id="71e41-119">描述</span><span class="sxs-lookup"><span data-stu-id="71e41-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="71e41-120">活動</span><span class="sxs-lookup"><span data-stu-id="71e41-120">Activity</span></span>|<span data-ttu-id="71e41-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="71e41-121">xs:string</span></span>|<span data-ttu-id="71e41-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="71e41-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="71e41-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="71e41-123">DisplayName</span></span>|<span data-ttu-id="71e41-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="71e41-124">xs:string</span></span>|<span data-ttu-id="71e41-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="71e41-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="71e41-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="71e41-126">InstanceId</span></span>|<span data-ttu-id="71e41-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="71e41-127">xs:string</span></span>|<span data-ttu-id="71e41-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="71e41-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="71e41-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="71e41-129">AppDomain</span></span>|<span data-ttu-id="71e41-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="71e41-130">xs:string</span></span>|<span data-ttu-id="71e41-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="71e41-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
