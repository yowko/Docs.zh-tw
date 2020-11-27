---
title: 設計和實作自訂活動
description: 本文提供的資源可讓您建立複合活動或建立新的活動類型，以在 Workflow Foundation 中建立自訂活動。
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: cb6e189cf5f59630ce8d89610eb0c2fc2acc92a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280386"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="67c00-103">設計和實作自訂活動</span><span class="sxs-lookup"><span data-stu-id="67c00-103">Designing and Implementing Custom Activities</span></span>

<span data-ttu-id="67c00-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中的自訂活動建立方法，是將系統提供的活動組合到複合活動中，或是建立衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的新型別。</span><span class="sxs-lookup"><span data-stu-id="67c00-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="67c00-105">本節描述如何以上述兩種方法建立自訂活動。</span><span class="sxs-lookup"><span data-stu-id="67c00-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67c00-106">在工作流程設計工具中，自訂活動預設會顯示成附有活動名稱的簡單矩形。</span><span class="sxs-lookup"><span data-stu-id="67c00-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="67c00-107">若要在工作流程設計工具中提供自訂的視覺化活動表示形式，您還必須建立自訂的設計工具。</span><span class="sxs-lookup"><span data-stu-id="67c00-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="67c00-108">如需詳細資訊，請參閱 [使用自訂活動設計工具和範本](using-custom-activity-designers-and-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="67c00-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67c00-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="67c00-109">In This Section</span></span>  

 [<span data-ttu-id="67c00-110">活動撰寫選項</span><span class="sxs-lookup"><span data-stu-id="67c00-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="67c00-111">討論 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中可用的撰寫樣式。</span><span class="sxs-lookup"><span data-stu-id="67c00-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="67c00-112">使用自訂活動</span><span class="sxs-lookup"><span data-stu-id="67c00-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="67c00-113">說明如何將自訂活動加入至工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="67c00-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="67c00-114">建立非同步活動</span><span class="sxs-lookup"><span data-stu-id="67c00-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="67c00-115">說明如何建立非同步活動。</span><span class="sxs-lookup"><span data-stu-id="67c00-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="67c00-116">設定活動驗證</span><span class="sxs-lookup"><span data-stu-id="67c00-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="67c00-117">說明如何使用活動驗證，在執行活動之前識別及報告活動組態中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="67c00-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="67c00-118">在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="67c00-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="67c00-119">討論如何在執行階段使用 <xref:System.Activities.DynamicActivity> 建立活動。</span><span class="sxs-lookup"><span data-stu-id="67c00-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="67c00-120">工作流程執行屬性</span><span class="sxs-lookup"><span data-stu-id="67c00-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="67c00-121">說明如何使用工作流程執行屬性，將內容特定屬性加入至活動的環境中</span><span class="sxs-lookup"><span data-stu-id="67c00-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="67c00-122">使用活動委派</span><span class="sxs-lookup"><span data-stu-id="67c00-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="67c00-123">討論如何編寫和使用包含活動委派的活動。</span><span class="sxs-lookup"><span data-stu-id="67c00-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="67c00-124">使用活動延伸模組</span><span class="sxs-lookup"><span data-stu-id="67c00-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="67c00-125">說明如何編寫和使用活動延伸模組。</span><span class="sxs-lookup"><span data-stu-id="67c00-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="67c00-126">從流程中使用 OData 摘要</span><span class="sxs-lookup"><span data-stu-id="67c00-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="67c00-127">說明從工作流程中呼叫 WCF 資料服務的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="67c00-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="67c00-128">活動定義範圍和可視性</span><span class="sxs-lookup"><span data-stu-id="67c00-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="67c00-129">說明定義資料範圍和活動成員可視性的選項及規則。</span><span class="sxs-lookup"><span data-stu-id="67c00-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
