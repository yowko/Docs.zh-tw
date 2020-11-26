---
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: aa4c7b2c98924eb43f78ab23a145b93906e302fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239805"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="db24c-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="db24c-102">1007 - WorkflowApplicationPersisted</span></span>

## <a name="properties"></a><span data-ttu-id="db24c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="db24c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db24c-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="db24c-104">ID</span></span>|<span data-ttu-id="db24c-105">1007</span><span class="sxs-lookup"><span data-stu-id="db24c-105">1007</span></span>|  
|<span data-ttu-id="db24c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="db24c-106">Keywords</span></span>|<span data-ttu-id="db24c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="db24c-107">WFRuntime</span></span>|  
|<span data-ttu-id="db24c-108">層級</span><span class="sxs-lookup"><span data-stu-id="db24c-108">Level</span></span>|<span data-ttu-id="db24c-109">資訊</span><span class="sxs-lookup"><span data-stu-id="db24c-109">Information</span></span>|  
|<span data-ttu-id="db24c-110">通路</span><span class="sxs-lookup"><span data-stu-id="db24c-110">Channel</span></span>|<span data-ttu-id="db24c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="db24c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db24c-112">描述</span><span class="sxs-lookup"><span data-stu-id="db24c-112">Description</span></span>  

 <span data-ttu-id="db24c-113">表示工作流程應用程式是永續性。</span><span class="sxs-lookup"><span data-stu-id="db24c-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db24c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="db24c-114">Message</span></span>  

 <span data-ttu-id="db24c-115">WorkflowApplication Id：'%1' 是永續性的。</span><span class="sxs-lookup"><span data-stu-id="db24c-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db24c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="db24c-116">Details</span></span>  
  
|<span data-ttu-id="db24c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="db24c-117">Data Item Name</span></span>|<span data-ttu-id="db24c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="db24c-118">Data Item Type</span></span>|<span data-ttu-id="db24c-119">描述</span><span class="sxs-lookup"><span data-stu-id="db24c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db24c-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="db24c-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="db24c-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="db24c-121">The workflow application id</span></span>|  
|<span data-ttu-id="db24c-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db24c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="db24c-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="db24c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
