---
title: HOW TO：在重新裝載的設計工具中顯示驗證錯誤
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761467"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>HOW TO：在重新裝載的設計工具中顯示驗證錯誤
本主題描述如何擷取及發行 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中的驗證錯誤。 這提供確認重新裝載設計工具中工作流程是否有效的程序。  
  
 這個工作分為兩個部分。 第一個部分是提供 <xref:System.Activities.Presentation.Validation.IValidationErrorService> 的實作。  這個介面有要實作一個重要方法 <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>，這個方法會將包含錯誤資訊的 <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> 物件清單傳遞至偵錯記錄檔。  在實作此介面之後，您可以將該實作的執行個體發行至編輯內容，藉此擷取錯誤資訊。  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>實作 IValidationErrorService 介面  
  
1. 以下是將驗證錯誤寫出至偵錯記錄檔的簡單實作程式碼範例。  
  
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
  
### <a name="publishing-to-the-editing-context"></a>發行至編輯內容  
  
1. 以下用來發行至編輯內容的程式碼。  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
