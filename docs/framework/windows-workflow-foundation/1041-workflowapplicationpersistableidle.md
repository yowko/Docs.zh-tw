---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="ec7fc-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="ec7fc-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="ec7fc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ec7fc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec7fc-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec7fc-104">ID</span></span>|<span data-ttu-id="ec7fc-105">1041</span><span class="sxs-lookup"><span data-stu-id="ec7fc-105">1041</span></span>|  
|<span data-ttu-id="ec7fc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ec7fc-106">Keywords</span></span>|<span data-ttu-id="ec7fc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ec7fc-107">WFRuntime</span></span>|  
|<span data-ttu-id="ec7fc-108">層級</span><span class="sxs-lookup"><span data-stu-id="ec7fc-108">Level</span></span>|<span data-ttu-id="ec7fc-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ec7fc-109">Information</span></span>|  
|<span data-ttu-id="ec7fc-110">通道</span><span class="sxs-lookup"><span data-stu-id="ec7fc-110">Channel</span></span>|<span data-ttu-id="ec7fc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ec7fc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec7fc-112">描述</span><span class="sxs-lookup"><span data-stu-id="ec7fc-112">Description</span></span>  
 <span data-ttu-id="ec7fc-113">表示工作流程應用程式處於閒置狀態且為永續性。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="ec7fc-114">工作流程應用程式將會閒置或持續。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec7fc-115">訊息</span><span class="sxs-lookup"><span data-stu-id="ec7fc-115">Message</span></span>  
 <span data-ttu-id="ec7fc-116">WorkflowApplication Id: '%1' 處於閒置狀態且可保存。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="ec7fc-117">將會採取下列動作: %2。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec7fc-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec7fc-118">Details</span></span>  
  
|<span data-ttu-id="ec7fc-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ec7fc-119">Data Item Name</span></span>|<span data-ttu-id="ec7fc-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ec7fc-120">Data Item Type</span></span>|<span data-ttu-id="ec7fc-121">描述</span><span class="sxs-lookup"><span data-stu-id="ec7fc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec7fc-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="ec7fc-122">WorkflowApplicationId</span></span>|<span data-ttu-id="ec7fc-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec7fc-123">xs:string</span></span>|<span data-ttu-id="ec7fc-124">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="ec7fc-124">The workflow application id</span></span>|  
|<span data-ttu-id="ec7fc-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="ec7fc-125">ActionTaken</span></span>|<span data-ttu-id="ec7fc-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec7fc-126">xs:string</span></span>|<span data-ttu-id="ec7fc-127">將要對工作流程應用程式要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="ec7fc-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec7fc-128">AppDomain</span></span>|<span data-ttu-id="ec7fc-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec7fc-129">xs:string</span></span>|<span data-ttu-id="ec7fc-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ec7fc-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
