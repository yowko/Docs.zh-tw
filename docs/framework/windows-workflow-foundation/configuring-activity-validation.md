---
title: "設定活動驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="149bc-102">設定活動驗證</span><span class="sxs-lookup"><span data-stu-id="149bc-102">Configuring Activity Validation</span></span>
<span data-ttu-id="149bc-103">活動驗證可讓活動作者和使用者在執行前，先在活動的組態中識別及報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="149bc-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="149bc-104"> 提供下列三種活動驗證：</span><span class="sxs-lookup"><span data-stu-id="149bc-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="149bc-105">`RequiredArgument` 與 `OverloadGroup` 屬性。</span><span class="sxs-lookup"><span data-stu-id="149bc-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="149bc-106">命令式的程式碼式驗證。</span><span class="sxs-lookup"><span data-stu-id="149bc-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="149bc-107">宣告式條件約束。</span><span class="sxs-lookup"><span data-stu-id="149bc-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="149bc-108">指出活動需要特定引數的 `RequiredArgument` 和 `OverloadGroup` 屬性。</span><span class="sxs-lookup"><span data-stu-id="149bc-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="149bc-109">命令式的程式碼式驗證提供讓活動自我驗證的簡易方式，而宣告式條件約束則可用於驗證活動及活動與包含該活動之工作流程的關聯性。</span><span class="sxs-lookup"><span data-stu-id="149bc-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="149bc-110">如果未根據驗證需求正確設定活動，就會傳回驗證錯誤與警告。</span><span class="sxs-lookup"><span data-stu-id="149bc-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="149bc-111">如果包含該活動的工作流程是使用工作流程設計工具建立的，則任何驗證錯誤與警告都會顯示在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="149bc-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="149bc-112">如果工作流程是在工作流程設計工具以外建立的，則會在叫用該工作流程時傳回所有驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="149bc-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="149bc-113">無論工作流程的建立方式為何，含驗證錯誤的工作流程永遠不能執行。</span><span class="sxs-lookup"><span data-stu-id="149bc-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="149bc-114">本節提供這些活動驗證類型與活動驗證叫用方式的概觀。</span><span class="sxs-lookup"><span data-stu-id="149bc-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="149bc-115">本章節內容</span><span class="sxs-lookup"><span data-stu-id="149bc-115">In This Section</span></span>  
 [<span data-ttu-id="149bc-116">必要引數與多載群組</span><span class="sxs-lookup"><span data-stu-id="149bc-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="149bc-117">描述如何使用 `RequiredArgument`和 `OverloadGroup` 屬性提供驗證。</span><span class="sxs-lookup"><span data-stu-id="149bc-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="149bc-118">命令式程式碼式驗證</span><span class="sxs-lookup"><span data-stu-id="149bc-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="149bc-119">描述如何將程式碼式的驗證用於 <xref:System.Activities.CodeActivity> 和 <xref:System.Activities.NativeActivity> 式的活動。</span><span class="sxs-lookup"><span data-stu-id="149bc-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="149bc-120">宣告式條件約束</span><span class="sxs-lookup"><span data-stu-id="149bc-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="149bc-121">描述如何使用宣告式條件約束提供複雜活動驗證。</span><span class="sxs-lookup"><span data-stu-id="149bc-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="149bc-122">叫用活動驗證</span><span class="sxs-lookup"><span data-stu-id="149bc-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="149bc-123">討論自動叫用活動驗證的時機，以及明確叫用驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="149bc-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="149bc-124">參考資料</span><span class="sxs-lookup"><span data-stu-id="149bc-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="149bc-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="149bc-125">Related Sections</span></span>
