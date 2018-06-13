---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510075"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="7e85f-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="7e85f-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="7e85f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7e85f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e85f-104">ID</span><span class="sxs-lookup"><span data-stu-id="7e85f-104">ID</span></span>|<span data-ttu-id="7e85f-105">1002</span><span class="sxs-lookup"><span data-stu-id="7e85f-105">1002</span></span>|  
|<span data-ttu-id="7e85f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e85f-106">Keywords</span></span>|<span data-ttu-id="7e85f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7e85f-107">WFRuntime</span></span>|  
|<span data-ttu-id="7e85f-108">層級</span><span class="sxs-lookup"><span data-stu-id="7e85f-108">Level</span></span>|<span data-ttu-id="7e85f-109">資訊</span><span class="sxs-lookup"><span data-stu-id="7e85f-109">Information</span></span>|  
|<span data-ttu-id="7e85f-110">通道</span><span class="sxs-lookup"><span data-stu-id="7e85f-110">Channel</span></span>|<span data-ttu-id="7e85f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7e85f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7e85f-112">描述</span><span class="sxs-lookup"><span data-stu-id="7e85f-112">Description</span></span>  
 <span data-ttu-id="7e85f-113">表示工作流程應用程式在 Faulted 狀態下終止，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e85f-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7e85f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7e85f-114">Message</span></span>  
 <span data-ttu-id="7e85f-115">WorkflowApplication Id：'%1' 已終止。</span><span class="sxs-lookup"><span data-stu-id="7e85f-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="7e85f-116">它已經以 Faulted 狀態完成，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e85f-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7e85f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e85f-117">Details</span></span>  
  
|<span data-ttu-id="7e85f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7e85f-118">Data Item Name</span></span>|<span data-ttu-id="7e85f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7e85f-119">Data Item Type</span></span>|<span data-ttu-id="7e85f-120">描述</span><span class="sxs-lookup"><span data-stu-id="7e85f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7e85f-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="7e85f-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="7e85f-122">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="7e85f-122">The workflow application id</span></span>|  
|<span data-ttu-id="7e85f-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7e85f-123">Exception</span></span>|`xs:string`|<span data-ttu-id="7e85f-124">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e85f-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="7e85f-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e85f-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7e85f-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7e85f-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
