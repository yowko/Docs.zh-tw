---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925225"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="b47d2-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="b47d2-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="b47d2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b47d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b47d2-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="b47d2-104">ID</span></span>|<span data-ttu-id="b47d2-105">1008</span><span class="sxs-lookup"><span data-stu-id="b47d2-105">1008</span></span>|  
|<span data-ttu-id="b47d2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b47d2-106">Keywords</span></span>|<span data-ttu-id="b47d2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b47d2-107">WFRuntime</span></span>|  
|<span data-ttu-id="b47d2-108">層級</span><span class="sxs-lookup"><span data-stu-id="b47d2-108">Level</span></span>|<span data-ttu-id="b47d2-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b47d2-109">Information</span></span>|  
|<span data-ttu-id="b47d2-110">通道</span><span class="sxs-lookup"><span data-stu-id="b47d2-110">Channel</span></span>|<span data-ttu-id="b47d2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b47d2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b47d2-112">描述</span><span class="sxs-lookup"><span data-stu-id="b47d2-112">Description</span></span>  
 <span data-ttu-id="b47d2-113">表示工作流程應用程式已卸載。</span><span class="sxs-lookup"><span data-stu-id="b47d2-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b47d2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b47d2-114">Message</span></span>  
 <span data-ttu-id="b47d2-115">WorkflowInstance Id：'%1' 已卸載。</span><span class="sxs-lookup"><span data-stu-id="b47d2-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b47d2-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b47d2-116">Details</span></span>  
  
|<span data-ttu-id="b47d2-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b47d2-117">Data Item Name</span></span>|<span data-ttu-id="b47d2-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b47d2-118">Data Item Type</span></span>|<span data-ttu-id="b47d2-119">描述</span><span class="sxs-lookup"><span data-stu-id="b47d2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b47d2-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b47d2-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b47d2-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b47d2-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b47d2-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b47d2-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b47d2-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b47d2-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
