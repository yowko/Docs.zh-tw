---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008599"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="31ad9-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="31ad9-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="31ad9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="31ad9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31ad9-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="31ad9-104">ID</span></span>|<span data-ttu-id="31ad9-105">1005</span><span class="sxs-lookup"><span data-stu-id="31ad9-105">1005</span></span>|  
|<span data-ttu-id="31ad9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="31ad9-106">Keywords</span></span>|<span data-ttu-id="31ad9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31ad9-107">WFRuntime</span></span>|  
|<span data-ttu-id="31ad9-108">層級</span><span class="sxs-lookup"><span data-stu-id="31ad9-108">Level</span></span>|<span data-ttu-id="31ad9-109">資訊</span><span class="sxs-lookup"><span data-stu-id="31ad9-109">Information</span></span>|  
|<span data-ttu-id="31ad9-110">通道</span><span class="sxs-lookup"><span data-stu-id="31ad9-110">Channel</span></span>|<span data-ttu-id="31ad9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="31ad9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31ad9-112">描述</span><span class="sxs-lookup"><span data-stu-id="31ad9-112">Description</span></span>  
 <span data-ttu-id="31ad9-113">表示工作流程應用程式已閒置。</span><span class="sxs-lookup"><span data-stu-id="31ad9-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31ad9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="31ad9-114">Message</span></span>  
 <span data-ttu-id="31ad9-115">WorkflowApplication Id：'%1' 閒置。</span><span class="sxs-lookup"><span data-stu-id="31ad9-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31ad9-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31ad9-116">Details</span></span>  
  
|<span data-ttu-id="31ad9-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="31ad9-117">Data Item Name</span></span>|<span data-ttu-id="31ad9-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="31ad9-118">Data Item Type</span></span>|<span data-ttu-id="31ad9-119">描述</span><span class="sxs-lookup"><span data-stu-id="31ad9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31ad9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="31ad9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="31ad9-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="31ad9-121">The workflow application id</span></span>|  
|<span data-ttu-id="31ad9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31ad9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="31ad9-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="31ad9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
