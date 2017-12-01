---
title: "取消可補償活動上的處理常式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 64d594711a805f75e1d76e59579032b0dc73dc93
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a>取消可補償活動上的處理常式
這個範例示範如何在 <xref:System.Activities.Statements.CompensableActivity> 上使用取消處理常式。  
  
 這個範例包含兩個示範 <xref:System.Activities.Statements.CompensableActivity> 取消用法的案例。第一個案例包含可補償的根活動，其中包含三個可補償的子活動。 兩個子活動成功完成執行其活動主體。 當第三個子活動主體執行時，遇到例外狀況，該例外狀況的處理方式是取消第三個活動處理，在此之後，會觸發根活動取消。 這個範例中根活動的邏輯是補償另外兩個稍早完成的子活動。  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 第二個案例示範如何平行執行 <xref:System.Activities.Statements.TryCatch> 與 <xref:System.Activities.Statements.Delay>，後者在 <xref:System.Activities.Statements.TryCatch> 分支之前完成。 一旦第一個分支完成，完成條件會設為 `true`，導致另一個分支取消。  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CompensationCancellation.sln。  
  
2.  按 CTRL+SHIFT+B 或選取 [建置] 功能表中的 [建置方案]，以建置範例。  
  
3.  按 F5 或選取 [偵錯] 功能表中的 [開始偵錯]，執行範例。 或者，您可以按 Ctrl+F5 或選取 [偵錯] 功能表中的 [啟動但不偵錯]。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`