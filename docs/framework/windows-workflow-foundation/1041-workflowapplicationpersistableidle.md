---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238934"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="ccf43-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="ccf43-102">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="ccf43-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ccf43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccf43-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="ccf43-104">ID</span></span>|<span data-ttu-id="ccf43-105">1041</span><span class="sxs-lookup"><span data-stu-id="ccf43-105">1041</span></span>|  
|<span data-ttu-id="ccf43-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ccf43-106">Keywords</span></span>|<span data-ttu-id="ccf43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ccf43-107">WFRuntime</span></span>|  
|<span data-ttu-id="ccf43-108">層級</span><span class="sxs-lookup"><span data-stu-id="ccf43-108">Level</span></span>|<span data-ttu-id="ccf43-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ccf43-109">Information</span></span>|  
|<span data-ttu-id="ccf43-110">通路</span><span class="sxs-lookup"><span data-stu-id="ccf43-110">Channel</span></span>|<span data-ttu-id="ccf43-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ccf43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ccf43-112">描述</span><span class="sxs-lookup"><span data-stu-id="ccf43-112">Description</span></span>  

 <span data-ttu-id="ccf43-113">表示工作流程應用程式處於閒置狀態且為永續性。</span><span class="sxs-lookup"><span data-stu-id="ccf43-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="ccf43-114">工作流程應用程式將會閒置或持續。</span><span class="sxs-lookup"><span data-stu-id="ccf43-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ccf43-115">訊息</span><span class="sxs-lookup"><span data-stu-id="ccf43-115">Message</span></span>  

 <span data-ttu-id="ccf43-116">WorkflowApplication 識別碼： ' %1 ' 為閒置和永久性。</span><span class="sxs-lookup"><span data-stu-id="ccf43-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="ccf43-117">將採取下列動作： %2。</span><span class="sxs-lookup"><span data-stu-id="ccf43-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ccf43-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ccf43-118">Details</span></span>  
  
|<span data-ttu-id="ccf43-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ccf43-119">Data Item Name</span></span>|<span data-ttu-id="ccf43-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ccf43-120">Data Item Type</span></span>|<span data-ttu-id="ccf43-121">描述</span><span class="sxs-lookup"><span data-stu-id="ccf43-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ccf43-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="ccf43-122">WorkflowApplicationId</span></span>|<span data-ttu-id="ccf43-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccf43-123">xs:string</span></span>|<span data-ttu-id="ccf43-124">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="ccf43-124">The workflow application id</span></span>|  
|<span data-ttu-id="ccf43-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="ccf43-125">ActionTaken</span></span>|<span data-ttu-id="ccf43-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccf43-126">xs:string</span></span>|<span data-ttu-id="ccf43-127">將要對工作流程應用程式要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ccf43-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="ccf43-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ccf43-128">AppDomain</span></span>|<span data-ttu-id="ccf43-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccf43-129">xs:string</span></span>|<span data-ttu-id="ccf43-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ccf43-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
