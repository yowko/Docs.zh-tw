---
title: "使用 InvokeMethod 活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 使用 InvokeMethod 活動
這個範例示範如何使用 <xref:System.Activities.Statements.InvokeMethod%601> 活動叫用公用類別中的公用方法。<xref:System.Activities.Statements.InvokeMethod%601> 活動允許工作流程針對物件呼叫方法、傳入參數、取得傳回值、指定泛型方法的類型，以及指定方法是同步或非同步。  
  
 非泛型 <xref:System.Activities.Statements.InvokeMethod> 活動版本的傳回值是設為 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 屬性，泛型 <xref:System.Activities.Statements.InvokeMethod%601> 活動版本的傳回值是透過 `TResult` 類型的 <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> 屬性來傳回。  
  
 這個範例示範如何呼叫各種方法類型。下列清單詳述這個範例中示範的方法類型。  
  
-   叫用不含參數的執行個體方法。  
  
-   叫用具有兩個參數 \(System.String 和 System.Int32\) 的執行個體方法。  
  
-   叫用具有兩個參數 \(System.String 和 System.Int32\) 以及 System.String\[\] 類型之參數陣列的執行個體方法。  
  
-   叫用具有兩個參數 \(兩個 System.Int32 數字\) 以及 System.Int32 類型之結果的執行個體方法。  
  
     傳回值是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。  
  
-   叫用具有兩個參數 \(System.String 和 System.Int32\) 的靜態方法。  
  
-   叫用具有一個泛型參數 \(System.String\) 的執行個體方法。  
  
-   叫用具有兩個泛型參數 \(System.String 和 System.Int32\) 的靜態方法。  
  
-   叫用執行個體方法，該方法的一個參數是以傳址方式傳遞 \(System.String\)。  
  
     參考的參數是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。  
  
-   叫用非同步執行個體方法。  
  
## 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 InvokeMethodUsage.sln 方案檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按下 CTRL\+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## 請參閱