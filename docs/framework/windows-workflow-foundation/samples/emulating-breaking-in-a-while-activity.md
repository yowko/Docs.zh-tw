---
title: "While 活動中的模擬中斷"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4417f4225200f01f23d753f6b7aa52ebc69cab4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="emulating-breaking-in-a-while-activity"></a>While 活動中的模擬中斷
這個範例會示範如何中斷下列活動的迴圈機制：<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While> 和 <xref:System.Activities.Statements.ParallelForEach%601>。  
  
 這項處理很實用，因為 [!INCLUDE[wf](../../../../includes/wf-md.md)] 不包括可中斷這些迴圈執行的任何活動。  
  
## <a name="scenario"></a>情節  
 此範例會從廠商清單中尋找第一家可靠的廠商 (`Vendor` 類別的執行個體)。 每一家廠商都有 `ID`、`Name` 以及數值信賴值 (可決定廠商的信賴度)。 此範例會建立一個名為 `FindReliableVendor` 的自訂活動，此活動會接收兩個輸入參數 (廠商清單及最低信賴值)，並傳回清單中符合提供之準則的第一家廠商。  
  
## <a name="breaking-a-loop"></a>中斷迴圈  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] 不包括可中斷迴圈的活動。 此程式碼範例會使用 <xref:System.Activities.Statements.If> 活動和幾個變數來完成中斷迴圈的工作。 在範例中，一旦 <xref:System.Activities.Statements.While> 變數指派了 `reliableVendor` 以外的值，`null` 活動就會中斷。  
  
 下列程式碼範例示範此範例如何中斷 while 迴圈。  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 EmulatingBreakInWhile.sln 方案檔。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`  
  
## <a name="see-also"></a>另請參閱
