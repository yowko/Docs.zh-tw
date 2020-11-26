---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 3b7210246b7fb754145c8aa6128da3183cea9f91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239857"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="7e7f3-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="7e7f3-102">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="7e7f3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7e7f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e7f3-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="7e7f3-104">ID</span></span>|<span data-ttu-id="7e7f3-105">1005</span><span class="sxs-lookup"><span data-stu-id="7e7f3-105">1005</span></span>|  
|<span data-ttu-id="7e7f3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e7f3-106">Keywords</span></span>|<span data-ttu-id="7e7f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7e7f3-107">WFRuntime</span></span>|  
|<span data-ttu-id="7e7f3-108">層級</span><span class="sxs-lookup"><span data-stu-id="7e7f3-108">Level</span></span>|<span data-ttu-id="7e7f3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="7e7f3-109">Information</span></span>|  
|<span data-ttu-id="7e7f3-110">通路</span><span class="sxs-lookup"><span data-stu-id="7e7f3-110">Channel</span></span>|<span data-ttu-id="7e7f3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7e7f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7e7f3-112">描述</span><span class="sxs-lookup"><span data-stu-id="7e7f3-112">Description</span></span>  

 <span data-ttu-id="7e7f3-113">表示工作流程應用程式已閒置。</span><span class="sxs-lookup"><span data-stu-id="7e7f3-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7e7f3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7e7f3-114">Message</span></span>  

 <span data-ttu-id="7e7f3-115">WorkflowApplication Id：'%1' 閒置。</span><span class="sxs-lookup"><span data-stu-id="7e7f3-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7e7f3-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e7f3-116">Details</span></span>  
  
|<span data-ttu-id="7e7f3-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7e7f3-117">Data Item Name</span></span>|<span data-ttu-id="7e7f3-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7e7f3-118">Data Item Type</span></span>|<span data-ttu-id="7e7f3-119">描述</span><span class="sxs-lookup"><span data-stu-id="7e7f3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7e7f3-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7e7f3-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="7e7f3-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="7e7f3-121">The workflow application id</span></span>|  
|<span data-ttu-id="7e7f3-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e7f3-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7e7f3-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7e7f3-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
