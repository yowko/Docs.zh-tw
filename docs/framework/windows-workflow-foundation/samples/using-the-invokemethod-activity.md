---
title: "使用 InvokeMethod 活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5d3f6734f9d6a3b0e2279b2bb6cca71141c8f5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-invokemethod-activity"></a>使用 InvokeMethod 活動
這個範例會示範如何使用<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動叫用公用類別中的公用方法。 <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動允許工作流程針對物件呼叫方法、 傳入參數、 取得傳回值、 指定泛型方法的類型和指定方法是否為同步或非同步的。 
  
非泛型版本<xref:System.Activities.Statements.InvokeMethod>活動傳回的值設定為其中<xref:System.Activities.Statements.InvokeMethod.Result%2A>屬性和泛型版本<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動傳回的傳回值的位置透過<!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx)型別的屬性`TResult`。 
  
 這個範例示範如何呼叫各種方法類型。 下列清單詳述這個範例中示範的方法類型。  
  
-   叫用不含參數的執行個體方法。  
  
-   叫用具有兩個參數 (System.String 和 System.Int32) 的執行個體方法。  
  
-   叫用具有兩個參數 (System.String 和 System.Int32) 以及 System.String[] 類型之參數陣列的執行個體方法。  
  
-   叫用具有兩個參數 (兩個 System.Int32 數字) 以及 System.Int32 類型之結果的執行個體方法。  
  
     傳回值是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。  
  
-   叫用具有兩個參數 (System.String 和 System.Int32) 的靜態方法。  
  
-   叫用具有一個泛型參數 (System.String) 的執行個體方法。  
  
-   叫用具有兩個泛型參數 (System.String 和 System.Int32) 的靜態方法。  
  
-   叫用執行個體方法，該方法的一個參數是以傳址方式傳遞 (System.String)。  
  
     參考的參數是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。  
  
-   叫用非同步執行個體方法。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 InvokeMethodUsage.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`