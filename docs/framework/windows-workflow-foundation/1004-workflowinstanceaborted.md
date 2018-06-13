---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510662"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="86c08-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="86c08-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="86c08-103">屬性</span><span class="sxs-lookup"><span data-stu-id="86c08-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86c08-104">ID</span><span class="sxs-lookup"><span data-stu-id="86c08-104">ID</span></span>|<span data-ttu-id="86c08-105">1004</span><span class="sxs-lookup"><span data-stu-id="86c08-105">1004</span></span>|  
|<span data-ttu-id="86c08-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="86c08-106">Keywords</span></span>|<span data-ttu-id="86c08-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="86c08-107">WFRuntime</span></span>|  
|<span data-ttu-id="86c08-108">層級</span><span class="sxs-lookup"><span data-stu-id="86c08-108">Level</span></span>|<span data-ttu-id="86c08-109">資訊</span><span class="sxs-lookup"><span data-stu-id="86c08-109">Information</span></span>|  
|<span data-ttu-id="86c08-110">通道</span><span class="sxs-lookup"><span data-stu-id="86c08-110">Channel</span></span>|<span data-ttu-id="86c08-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="86c08-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86c08-112">描述</span><span class="sxs-lookup"><span data-stu-id="86c08-112">Description</span></span>  
 <span data-ttu-id="86c08-113">表示工作流程執行個體已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86c08-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86c08-114">訊息</span><span class="sxs-lookup"><span data-stu-id="86c08-114">Message</span></span>  
 <span data-ttu-id="86c08-115">WorkflowInstance Id：'%1' 已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86c08-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86c08-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="86c08-116">Details</span></span>  
  
|<span data-ttu-id="86c08-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="86c08-117">Data Item Name</span></span>|<span data-ttu-id="86c08-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="86c08-118">Data Item Type</span></span>|<span data-ttu-id="86c08-119">描述</span><span class="sxs-lookup"><span data-stu-id="86c08-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86c08-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="86c08-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="86c08-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="86c08-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="86c08-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="86c08-122">Exception</span></span>|`xs:string`|<span data-ttu-id="86c08-123">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="86c08-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="86c08-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86c08-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="86c08-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="86c08-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
