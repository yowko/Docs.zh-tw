---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509791"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="7c3e8-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="7c3e8-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="7c3e8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7c3e8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c3e8-104">ID</span><span class="sxs-lookup"><span data-stu-id="7c3e8-104">ID</span></span>|<span data-ttu-id="7c3e8-105">1001</span><span class="sxs-lookup"><span data-stu-id="7c3e8-105">1001</span></span>|  
|<span data-ttu-id="7c3e8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7c3e8-106">Keywords</span></span>|<span data-ttu-id="7c3e8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7c3e8-107">WFRuntime</span></span>|  
|<span data-ttu-id="7c3e8-108">層級</span><span class="sxs-lookup"><span data-stu-id="7c3e8-108">Level</span></span>|<span data-ttu-id="7c3e8-109">資訊</span><span class="sxs-lookup"><span data-stu-id="7c3e8-109">Information</span></span>|  
|<span data-ttu-id="7c3e8-110">通道</span><span class="sxs-lookup"><span data-stu-id="7c3e8-110">Channel</span></span>|<span data-ttu-id="7c3e8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7c3e8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c3e8-112">描述</span><span class="sxs-lookup"><span data-stu-id="7c3e8-112">Description</span></span>  
 <span data-ttu-id="7c3e8-113">表示工作流程應用程式已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="7c3e8-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c3e8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7c3e8-114">Message</span></span>  
 <span data-ttu-id="7c3e8-115">WorkflowInstance Id：'%1' 已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="7c3e8-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c3e8-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7c3e8-116">Details</span></span>  
  
|<span data-ttu-id="7c3e8-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7c3e8-117">Data Item Name</span></span>|<span data-ttu-id="7c3e8-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7c3e8-118">Data Item Type</span></span>|<span data-ttu-id="7c3e8-119">描述</span><span class="sxs-lookup"><span data-stu-id="7c3e8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c3e8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7c3e8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="7c3e8-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7c3e8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="7c3e8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c3e8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7c3e8-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7c3e8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
