---
title: "HOW TO：在重新裝載的設計工具中顯示驗證錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9f76f1ad5282ecf10a3ce58db0f6e1bd8df1b4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="0f6fd-102">HOW TO：在重新裝載的設計工具中顯示驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="0f6fd-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="0f6fd-103">本主題描述如何擷取及發行 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中的驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="0f6fd-104">這提供確認重新裝載設計工具中工作流程是否有效的程序。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="0f6fd-105">這個工作分為兩個部分。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-105">This task has two parts.</span></span> <span data-ttu-id="0f6fd-106">第一個部分是提供 <xref:System.Activities.Presentation.Validation.IValidationErrorService> 的實作。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="0f6fd-107">這個介面有要實作一個重要方法 <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>，這個方法會將包含錯誤資訊的 <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> 物件清單傳遞至偵錯記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="0f6fd-108">在實作此介面之後，您可以將該實作的執行個體發行至編輯內容，藉此擷取錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="0f6fd-109">實作 IValidationErrorService 介面</span><span class="sxs-lookup"><span data-stu-id="0f6fd-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="0f6fd-110">以下是將驗證錯誤寫出至偵錯記錄檔的簡單實作程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="0f6fd-111">發行至編輯內容</span><span class="sxs-lookup"><span data-stu-id="0f6fd-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="0f6fd-112">以下用來發行至編輯內容的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f6fd-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
