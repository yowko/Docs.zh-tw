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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="3204b-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="3204b-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="3204b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3204b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3204b-104">ID</span><span class="sxs-lookup"><span data-stu-id="3204b-104">ID</span></span>|<span data-ttu-id="3204b-105">1041</span><span class="sxs-lookup"><span data-stu-id="3204b-105">1041</span></span>|  
|<span data-ttu-id="3204b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3204b-106">Keywords</span></span>|<span data-ttu-id="3204b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3204b-107">WFRuntime</span></span>|  
|<span data-ttu-id="3204b-108">層級</span><span class="sxs-lookup"><span data-stu-id="3204b-108">Level</span></span>|<span data-ttu-id="3204b-109">資訊</span><span class="sxs-lookup"><span data-stu-id="3204b-109">Information</span></span>|  
|<span data-ttu-id="3204b-110">通道</span><span class="sxs-lookup"><span data-stu-id="3204b-110">Channel</span></span>|<span data-ttu-id="3204b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3204b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3204b-112">描述</span><span class="sxs-lookup"><span data-stu-id="3204b-112">Description</span></span>  
 <span data-ttu-id="3204b-113">表示工作流程應用程式處於閒置狀態且為永續性。</span><span class="sxs-lookup"><span data-stu-id="3204b-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="3204b-114">工作流程應用程式將會閒置或持續。</span><span class="sxs-lookup"><span data-stu-id="3204b-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3204b-115">訊息</span><span class="sxs-lookup"><span data-stu-id="3204b-115">Message</span></span>  
 <span data-ttu-id="3204b-116">WorkflowApplication Id: '%1' 處於閒置狀態且可保存。</span><span class="sxs-lookup"><span data-stu-id="3204b-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="3204b-117">將會採取下列動作: %2。</span><span class="sxs-lookup"><span data-stu-id="3204b-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3204b-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3204b-118">Details</span></span>  
  
|<span data-ttu-id="3204b-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3204b-119">Data Item Name</span></span>|<span data-ttu-id="3204b-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3204b-120">Data Item Type</span></span>|<span data-ttu-id="3204b-121">描述</span><span class="sxs-lookup"><span data-stu-id="3204b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3204b-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="3204b-122">WorkflowApplicationId</span></span>|<span data-ttu-id="3204b-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="3204b-123">xs:string</span></span>|<span data-ttu-id="3204b-124">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="3204b-124">The workflow application id</span></span>|  
|<span data-ttu-id="3204b-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="3204b-125">ActionTaken</span></span>|<span data-ttu-id="3204b-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="3204b-126">xs:string</span></span>|<span data-ttu-id="3204b-127">將要對工作流程應用程式要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="3204b-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="3204b-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3204b-128">AppDomain</span></span>|<span data-ttu-id="3204b-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="3204b-129">xs:string</span></span>|<span data-ttu-id="3204b-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3204b-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
