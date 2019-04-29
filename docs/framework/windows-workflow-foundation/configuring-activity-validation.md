---
title: 設定活動驗證
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774169"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="b9dc8-102">設定活動驗證</span><span class="sxs-lookup"><span data-stu-id="b9dc8-102">Configuring Activity Validation</span></span>
<span data-ttu-id="b9dc8-103">活動驗證可讓活動作者和使用者在執行前，先在活動的組態中識別及報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="b9dc8-104">Windows Workflow Foundation (WF) 提供下列三種活動驗證類型：</span><span class="sxs-lookup"><span data-stu-id="b9dc8-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="b9dc8-105">`RequiredArgument` 與 `OverloadGroup` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="b9dc8-106">命令式的程式碼式驗證。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-106">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="b9dc8-107">宣告式條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="b9dc8-108">指出活動需要特定引數的 `RequiredArgument` 和 `OverloadGroup` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="b9dc8-109">命令式的程式碼式驗證提供讓活動自我驗證的簡易方式，而宣告式條件約束則可用於驗證活動及活動與包含該活動之工作流程的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="b9dc8-110">如果未根據驗證需求正確設定活動，就會傳回驗證錯誤與警告。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="b9dc8-111">如果包含該活動的工作流程是使用工作流程設計工具建立的，則任何驗證錯誤與警告都會顯示在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="b9dc8-112">如果工作流程是在工作流程設計工具以外建立的，則會在叫用該工作流程時傳回所有驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="b9dc8-113">無論工作流程的建立方式為何，含驗證錯誤的工作流程永遠不能執行。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="b9dc8-114">本節提供這些活動驗證類型與活動驗證叫用方式的概觀。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9dc8-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="b9dc8-115">In This Section</span></span>  
 [<span data-ttu-id="b9dc8-116">必要引數與多載群組</span><span class="sxs-lookup"><span data-stu-id="b9dc8-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="b9dc8-117">描述如何使用 `RequiredArgument`和 `OverloadGroup` 屬性提供驗證。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="b9dc8-118">命令式程式碼式驗證</span><span class="sxs-lookup"><span data-stu-id="b9dc8-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="b9dc8-119">描述如何將程式碼式的驗證用於 <xref:System.Activities.CodeActivity> 和 <xref:System.Activities.NativeActivity> 式的活動。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="b9dc8-120">宣告式條件約束</span><span class="sxs-lookup"><span data-stu-id="b9dc8-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="b9dc8-121">描述如何使用宣告式條件約束提供複雜活動驗證。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="b9dc8-122">叫用活動驗證</span><span class="sxs-lookup"><span data-stu-id="b9dc8-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="b9dc8-123">討論自動叫用活動驗證的時機，以及明確叫用驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="b9dc8-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b9dc8-124">參考資料</span><span class="sxs-lookup"><span data-stu-id="b9dc8-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9dc8-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="b9dc8-125">Related Sections</span></span>
