---
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 0b3c290ad06eda6921626c0d7a1c8ec854c30e7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509713"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="21742-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="21742-102">1007 - WorkflowApplicationPersisted</span></span>
## <a name="properties"></a><span data-ttu-id="21742-103">屬性</span><span class="sxs-lookup"><span data-stu-id="21742-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21742-104">ID</span><span class="sxs-lookup"><span data-stu-id="21742-104">ID</span></span>|<span data-ttu-id="21742-105">1007</span><span class="sxs-lookup"><span data-stu-id="21742-105">1007</span></span>|  
|<span data-ttu-id="21742-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="21742-106">Keywords</span></span>|<span data-ttu-id="21742-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="21742-107">WFRuntime</span></span>|  
|<span data-ttu-id="21742-108">層級</span><span class="sxs-lookup"><span data-stu-id="21742-108">Level</span></span>|<span data-ttu-id="21742-109">資訊</span><span class="sxs-lookup"><span data-stu-id="21742-109">Information</span></span>|  
|<span data-ttu-id="21742-110">通道</span><span class="sxs-lookup"><span data-stu-id="21742-110">Channel</span></span>|<span data-ttu-id="21742-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="21742-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21742-112">描述</span><span class="sxs-lookup"><span data-stu-id="21742-112">Description</span></span>  
 <span data-ttu-id="21742-113">表示工作流程應用程式是永續性。</span><span class="sxs-lookup"><span data-stu-id="21742-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21742-114">訊息</span><span class="sxs-lookup"><span data-stu-id="21742-114">Message</span></span>  
 <span data-ttu-id="21742-115">WorkflowApplication Id：'%1' 是永續性的。</span><span class="sxs-lookup"><span data-stu-id="21742-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21742-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="21742-116">Details</span></span>  
  
|<span data-ttu-id="21742-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="21742-117">Data Item Name</span></span>|<span data-ttu-id="21742-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="21742-118">Data Item Type</span></span>|<span data-ttu-id="21742-119">描述</span><span class="sxs-lookup"><span data-stu-id="21742-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21742-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="21742-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="21742-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="21742-121">The workflow application id</span></span>|  
|<span data-ttu-id="21742-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21742-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="21742-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="21742-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
