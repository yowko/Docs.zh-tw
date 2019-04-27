---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924705"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="1a537-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="1a537-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="1a537-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1a537-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a537-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="1a537-104">ID</span></span>|<span data-ttu-id="1a537-105">1006</span><span class="sxs-lookup"><span data-stu-id="1a537-105">1006</span></span>|  
|<span data-ttu-id="1a537-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a537-106">Keywords</span></span>|<span data-ttu-id="1a537-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1a537-107">WFRuntime</span></span>|  
|<span data-ttu-id="1a537-108">層級</span><span class="sxs-lookup"><span data-stu-id="1a537-108">Level</span></span>|<span data-ttu-id="1a537-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="1a537-109">Error</span></span>|  
|<span data-ttu-id="1a537-110">通道</span><span class="sxs-lookup"><span data-stu-id="1a537-110">Channel</span></span>|<span data-ttu-id="1a537-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1a537-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1a537-112">描述</span><span class="sxs-lookup"><span data-stu-id="1a537-112">Description</span></span>  
 <span data-ttu-id="1a537-113">表示工作流程應用程式發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1a537-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1a537-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1a537-114">Message</span></span>  
 <span data-ttu-id="1a537-115">WorkflowInstance Id: '%1' 發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1a537-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="1a537-116">例外狀況源自活動 '%2'，DisplayName: '%3'。</span><span class="sxs-lookup"><span data-stu-id="1a537-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="1a537-117">將會採取下列動作: %4。</span><span class="sxs-lookup"><span data-stu-id="1a537-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1a537-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1a537-118">Details</span></span>  
  
|<span data-ttu-id="1a537-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1a537-119">Data Item Name</span></span>|<span data-ttu-id="1a537-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1a537-120">Data Item Type</span></span>|<span data-ttu-id="1a537-121">描述</span><span class="sxs-lookup"><span data-stu-id="1a537-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1a537-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="1a537-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="1a537-123">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1a537-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="1a537-124">例外</span><span class="sxs-lookup"><span data-stu-id="1a537-124">Exception</span></span>|`xs:string`|<span data-ttu-id="1a537-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="1a537-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="1a537-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1a537-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1a537-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1a537-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
