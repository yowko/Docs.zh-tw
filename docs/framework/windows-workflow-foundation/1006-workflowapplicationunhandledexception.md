---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239830"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="f2377-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="f2377-102">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="f2377-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f2377-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2377-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f2377-104">ID</span></span>|<span data-ttu-id="f2377-105">1006</span><span class="sxs-lookup"><span data-stu-id="f2377-105">1006</span></span>|  
|<span data-ttu-id="f2377-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f2377-106">Keywords</span></span>|<span data-ttu-id="f2377-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f2377-107">WFRuntime</span></span>|  
|<span data-ttu-id="f2377-108">層級</span><span class="sxs-lookup"><span data-stu-id="f2377-108">Level</span></span>|<span data-ttu-id="f2377-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="f2377-109">Error</span></span>|  
|<span data-ttu-id="f2377-110">通路</span><span class="sxs-lookup"><span data-stu-id="f2377-110">Channel</span></span>|<span data-ttu-id="f2377-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f2377-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2377-112">描述</span><span class="sxs-lookup"><span data-stu-id="f2377-112">Description</span></span>  

 <span data-ttu-id="f2377-113">表示工作流程應用程式發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2377-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2377-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f2377-114">Message</span></span>  

 <span data-ttu-id="f2377-115">WorkflowInstance 識別碼： ' %1 ' 發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2377-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="f2377-116">例外狀況源自活動 ' %2 '、DisplayName： ' %3 '。</span><span class="sxs-lookup"><span data-stu-id="f2377-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="f2377-117">將採取下列動作： %4。</span><span class="sxs-lookup"><span data-stu-id="f2377-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2377-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2377-118">Details</span></span>  
  
|<span data-ttu-id="f2377-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f2377-119">Data Item Name</span></span>|<span data-ttu-id="f2377-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f2377-120">Data Item Type</span></span>|<span data-ttu-id="f2377-121">描述</span><span class="sxs-lookup"><span data-stu-id="f2377-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2377-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="f2377-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="f2377-123">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f2377-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f2377-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f2377-124">Exception</span></span>|`xs:string`|<span data-ttu-id="f2377-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2377-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="f2377-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f2377-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f2377-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f2377-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
