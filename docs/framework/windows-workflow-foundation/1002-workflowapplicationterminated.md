---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: e7c92dcc9ce472c50af6f0aa26c59f55d62fbb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239935"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="5bd46-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="5bd46-102">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="5bd46-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5bd46-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bd46-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5bd46-104">ID</span></span>|<span data-ttu-id="5bd46-105">1002</span><span class="sxs-lookup"><span data-stu-id="5bd46-105">1002</span></span>|  
|<span data-ttu-id="5bd46-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5bd46-106">Keywords</span></span>|<span data-ttu-id="5bd46-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5bd46-107">WFRuntime</span></span>|  
|<span data-ttu-id="5bd46-108">層級</span><span class="sxs-lookup"><span data-stu-id="5bd46-108">Level</span></span>|<span data-ttu-id="5bd46-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5bd46-109">Information</span></span>|  
|<span data-ttu-id="5bd46-110">通路</span><span class="sxs-lookup"><span data-stu-id="5bd46-110">Channel</span></span>|<span data-ttu-id="5bd46-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5bd46-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5bd46-112">描述</span><span class="sxs-lookup"><span data-stu-id="5bd46-112">Description</span></span>  

 <span data-ttu-id="5bd46-113">表示工作流程應用程式在 Faulted 狀態下終止，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5bd46-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5bd46-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5bd46-114">Message</span></span>  

 <span data-ttu-id="5bd46-115">WorkflowApplication Id：'%1' 已終止。</span><span class="sxs-lookup"><span data-stu-id="5bd46-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="5bd46-116">它已經以 Faulted 狀態完成，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5bd46-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5bd46-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5bd46-117">Details</span></span>  
  
|<span data-ttu-id="5bd46-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5bd46-118">Data Item Name</span></span>|<span data-ttu-id="5bd46-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5bd46-119">Data Item Type</span></span>|<span data-ttu-id="5bd46-120">描述</span><span class="sxs-lookup"><span data-stu-id="5bd46-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5bd46-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="5bd46-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="5bd46-122">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="5bd46-122">The workflow application id</span></span>|  
|<span data-ttu-id="5bd46-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="5bd46-123">Exception</span></span>|`xs:string`|<span data-ttu-id="5bd46-124">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="5bd46-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="5bd46-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5bd46-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5bd46-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5bd46-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
