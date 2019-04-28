---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008638"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="77cb2-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="77cb2-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="77cb2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="77cb2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77cb2-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="77cb2-104">ID</span></span>|<span data-ttu-id="77cb2-105">1001</span><span class="sxs-lookup"><span data-stu-id="77cb2-105">1001</span></span>|  
|<span data-ttu-id="77cb2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="77cb2-106">Keywords</span></span>|<span data-ttu-id="77cb2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="77cb2-107">WFRuntime</span></span>|  
|<span data-ttu-id="77cb2-108">層級</span><span class="sxs-lookup"><span data-stu-id="77cb2-108">Level</span></span>|<span data-ttu-id="77cb2-109">資訊</span><span class="sxs-lookup"><span data-stu-id="77cb2-109">Information</span></span>|  
|<span data-ttu-id="77cb2-110">通道</span><span class="sxs-lookup"><span data-stu-id="77cb2-110">Channel</span></span>|<span data-ttu-id="77cb2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="77cb2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77cb2-112">描述</span><span class="sxs-lookup"><span data-stu-id="77cb2-112">Description</span></span>  
 <span data-ttu-id="77cb2-113">表示工作流程應用程式已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="77cb2-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77cb2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="77cb2-114">Message</span></span>  
 <span data-ttu-id="77cb2-115">WorkflowInstance Id：'%1' 已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="77cb2-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77cb2-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77cb2-116">Details</span></span>  
  
|<span data-ttu-id="77cb2-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="77cb2-117">Data Item Name</span></span>|<span data-ttu-id="77cb2-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="77cb2-118">Data Item Type</span></span>|<span data-ttu-id="77cb2-119">描述</span><span class="sxs-lookup"><span data-stu-id="77cb2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77cb2-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="77cb2-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="77cb2-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="77cb2-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="77cb2-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77cb2-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="77cb2-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="77cb2-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
