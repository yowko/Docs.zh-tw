---
title: "使用 CodeActivity 類別撰寫工作流程活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 使用 CodeActivity 類別撰寫工作流程活動
繼承自 <xref:System.Activities.CodeActivity> 所建立的活動可藉由覆寫 <xref:System.Activities.CodeActivity.Execute%2A> 方法來實作基本命令式行為。  
  
## 使用 CodeActivityContext  
 工作流程執行階段的功能可透過 <xref:System.Activities.CodeActivity.Execute%2A> 方法內部存取，方法是使用 `context` 參數的成員 \(型別為 <xref:System.Activities.CodeActivityContext>\)。透過 <xref:System.Activities.CodeActivityContext> 可使用的功能如下：  
  
-   取得與設定引數和變數的值。  
  
-   使用 <xref:System.Activities.CodeActivityContext.Track%2A> 自訂追蹤功能。  
  
-   使用 <xref:System.Activities.CodeActivityContext.GetProperty%2A> 存取活動的執行屬性。  
  
#### 若要建立繼承自 CodeActivity 的自訂活動  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  依序選取 \[**檔案**\]、\[**新增**\]、\[**專案**\]。在 \[**專案類型**\] 視窗中，選取 \[**Visual C\#**\] 下方 \[**Workflow 4.0**\]，然後選取 \[**v2010**\] 節點。選取 \[**範本**\] 視窗中的 \[**活動程式庫**\]。將新專案命名為 HelloActivity。  
  
3.  以滑鼠右鍵按一下 HelloActivity 專案中的 Activity1.xaml，然後選取 \[**刪除**\]。  
  
4.  以滑鼠右鍵按一下 HelloActivity 專案並選取 \[**加入**\]，然後選取 \[**類別**\]。將新類別命名為 HelloActivity.cs。  
  
5.  在 HelloActivity.cs 檔案中加入下列 `using` 指示詞。  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  將基底類別加入至類別宣告，使新的類別繼承自 <xref:System.Activities.CodeActivity>。  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  新增 <xref:System.Activities.CodeActivity.Execute%2A> 方法，將功能加入至類別中。  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  使用 <xref:System.Activities.CodeActivityContext> 建立追蹤記錄。  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
  
    ```