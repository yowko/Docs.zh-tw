---
title: 設計和實作自訂活動
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 2ed80b5cbb27c6647053ee9b8f4cd2bedb0c6cde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513810"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="86e9d-102">設計和實作自訂活動</span><span class="sxs-lookup"><span data-stu-id="86e9d-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="86e9d-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中的自訂活動建立方法，是將系統提供的活動組合到複合活動中，或是建立衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的新型別。</span><span class="sxs-lookup"><span data-stu-id="86e9d-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="86e9d-104">本節描述如何以上述兩種方法建立自訂活動。</span><span class="sxs-lookup"><span data-stu-id="86e9d-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="86e9d-105">在工作流程設計工具中，自訂活動預設會顯示成附有活動名稱的簡單矩形。</span><span class="sxs-lookup"><span data-stu-id="86e9d-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="86e9d-106">若要在工作流程設計工具中提供自訂的視覺化活動表示形式，您還必須建立自訂的設計工具。</span><span class="sxs-lookup"><span data-stu-id="86e9d-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="86e9d-107">如需詳細資訊，請參閱[使用自訂活動設計工具和範本](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="86e9d-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86e9d-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="86e9d-108">In This Section</span></span>  
 [<span data-ttu-id="86e9d-109">活動撰寫選項</span><span class="sxs-lookup"><span data-stu-id="86e9d-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="86e9d-110">討論 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中可用的撰寫樣式。</span><span class="sxs-lookup"><span data-stu-id="86e9d-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="86e9d-111">使用自訂活動</span><span class="sxs-lookup"><span data-stu-id="86e9d-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="86e9d-112">說明如何將自訂活動加入至工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="86e9d-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="86e9d-113">建立非同步活動</span><span class="sxs-lookup"><span data-stu-id="86e9d-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="86e9d-114">說明如何建立非同步活動。</span><span class="sxs-lookup"><span data-stu-id="86e9d-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="86e9d-115">設定活動驗證</span><span class="sxs-lookup"><span data-stu-id="86e9d-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="86e9d-116">說明如何使用活動驗證，在執行活動之前識別及報告活動組態中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="86e9d-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="86e9d-117">於執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="86e9d-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="86e9d-118">討論如何在執行階段使用 <xref:System.Activities.DynamicActivity> 建立活動。</span><span class="sxs-lookup"><span data-stu-id="86e9d-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="86e9d-119">工作流程執行屬性</span><span class="sxs-lookup"><span data-stu-id="86e9d-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="86e9d-120">說明如何使用工作流程執行屬性，將內容特定屬性加入至活動的環境中</span><span class="sxs-lookup"><span data-stu-id="86e9d-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="86e9d-121">使用活動委派</span><span class="sxs-lookup"><span data-stu-id="86e9d-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="86e9d-122">討論如何編寫和使用包含活動委派的活動。</span><span class="sxs-lookup"><span data-stu-id="86e9d-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="86e9d-123">活動當地語系化</span><span class="sxs-lookup"><span data-stu-id="86e9d-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="86e9d-124">說明如何在活動中使用當地語系化的字串資源。</span><span class="sxs-lookup"><span data-stu-id="86e9d-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="86e9d-125">使用活動延伸模組</span><span class="sxs-lookup"><span data-stu-id="86e9d-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="86e9d-126">說明如何編寫和使用活動延伸模組。</span><span class="sxs-lookup"><span data-stu-id="86e9d-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="86e9d-127">從工作流程使用 OData 摘要</span><span class="sxs-lookup"><span data-stu-id="86e9d-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="86e9d-128">說明從工作流程中呼叫 WCF 資料服務的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="86e9d-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="86e9d-129">活動定義範圍與可見度</span><span class="sxs-lookup"><span data-stu-id="86e9d-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="86e9d-130">說明定義資料範圍和活動成員可視性的選項及規則。</span><span class="sxs-lookup"><span data-stu-id="86e9d-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
