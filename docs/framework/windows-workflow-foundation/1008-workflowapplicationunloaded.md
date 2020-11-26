---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239817"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="c307a-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="c307a-102">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="c307a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c307a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c307a-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c307a-104">ID</span></span>|<span data-ttu-id="c307a-105">1008</span><span class="sxs-lookup"><span data-stu-id="c307a-105">1008</span></span>|  
|<span data-ttu-id="c307a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c307a-106">Keywords</span></span>|<span data-ttu-id="c307a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c307a-107">WFRuntime</span></span>|  
|<span data-ttu-id="c307a-108">層級</span><span class="sxs-lookup"><span data-stu-id="c307a-108">Level</span></span>|<span data-ttu-id="c307a-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c307a-109">Information</span></span>|  
|<span data-ttu-id="c307a-110">通路</span><span class="sxs-lookup"><span data-stu-id="c307a-110">Channel</span></span>|<span data-ttu-id="c307a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c307a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c307a-112">描述</span><span class="sxs-lookup"><span data-stu-id="c307a-112">Description</span></span>  

 <span data-ttu-id="c307a-113">表示工作流程應用程式已卸載。</span><span class="sxs-lookup"><span data-stu-id="c307a-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c307a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c307a-114">Message</span></span>  

 <span data-ttu-id="c307a-115">WorkflowInstance Id：'%1' 已卸載。</span><span class="sxs-lookup"><span data-stu-id="c307a-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c307a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c307a-116">Details</span></span>  
  
|<span data-ttu-id="c307a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c307a-117">Data Item Name</span></span>|<span data-ttu-id="c307a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c307a-118">Data Item Type</span></span>|<span data-ttu-id="c307a-119">描述</span><span class="sxs-lookup"><span data-stu-id="c307a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c307a-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c307a-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c307a-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c307a-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c307a-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c307a-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c307a-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c307a-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
