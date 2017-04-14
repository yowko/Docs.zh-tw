---
title: "使用 DynamicActivity 在執行階段建立活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 使用 DynamicActivity 在執行階段建立活動
<xref:System.Activities.DynamicActivity>是含公用建構函式的具體密封類別。<xref:System.Activities.DynamicActivity>可用於在執行階段中使用活動 DOM 組合活動功能。  
  
## DynamicActivity 功能  
 <xref:System.Activities.DynamicActivity> 可以存取執行屬性、引數和變數，但不可以存取執行階段服務，例如排定子活動或追蹤。  
  
 最上層的屬性可以使用工作流程 <xref:System.Activities.Argument> 物件來設定。在命令式程式碼中，這些引數是使用新型別的 CLR 屬性建立的。在 XAML 中，這些引數則是使用 `x:Class` 和 `x:Member` 標籤宣告的。  
  
 使用 <xref:System.Activities.DynamicActivity> 介面建構的活動，此介面具有使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 的設計工具。在設計工具中建立的活動可使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 動態載入，如下列程序中的示範。  
  
#### 若要使用命令式程式碼在執行階段建立活動  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  依序選取 \[**檔案**\]、\[**新增**\]、\[**專案**\]。在 \[**專案類型**\] 視窗中，選取 \[**Visual C\#**\] 下方 \[**Workflow 4.0**\]，然後選取 \[**v2010**\] 節點。選取 \[**範本**\] 視窗中的 \[**循序工作流程主控台應用程式**\]。將新專案命名為 DynamicActivitySample。  
  
3.  以滑鼠右鍵按一下 HelloActivity 專案中的 Workflow1.xaml，然後選取 \[**刪除**\]。  
  
4.  開啟 Program.cs。將下列指示詞加入至檔案的頂端。  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  以下列程式碼取代 `Main` 方法的內容，此程式碼會建立 <xref:System.Activities.Statements.Sequence> 活動 \(包含單一 <xref:System.Activities.Statements.WriteLine> 活動\)，並將該活動指派至新的動態活動之 <xref:System.Activities.DynamicActivity.Implementation%2A> 屬性。  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
  
    ```  
  
6.  執行應用程式。隨即顯示含有 “Hello World\!” 文字的主控台視窗。  
  
#### 若要使用 XAML 在執行階段建立活動  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  依序選取 \[**檔案**\]、\[**新增**\]、\[**專案**\]。在 \[**專案類型**\] 視窗中，選取 \[**Visual C\#**\] 下方 \[**Workflow 4.0**\]，然後選取 \[**v2010**\] 節點。選取 \[**範本**\] 視窗中的 \[**工作流程主控台應用程式**\]。將新專案命名為 DynamicActivitySample。  
  
3.  開啟 HelloActivity 專案中的 Workflow1.xaml。按一下設計工具底部的 \[**引數**\] 選項。建立新的 `In` 引數，其名稱為 `TextToWrite`、型別為 `String`。  
  
4.  將工具箱中 \[**基本**\] 區段的 \[**WriteLine**\] 活動拖曳至設計工具介面上。將 `TextToWrite` 值指派給活動的 \[**Text**屬性。  
  
5.  開啟 Program.cs。將下列指示詞加入至檔案的頂端。  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  以下列程式碼取代 `Main` 方法的內容。  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  執行應用程式。隨即出現含有 “Hello World\!” 文字的主控台視窗。  
  
8.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 Workflow1.xaml，然後選取 \[**檢視程式碼**\]。請注意，活動類別是以 `x:Class` 建立的，而屬性則是以 `x:Property` 建立的。  
  
## 請參閱  
 [使用命令式程式碼撰寫工作流程、活動和運算式](../../../docs/framework/windows-workflow-foundation//authoring-workflows-activities-and-expressions-using-imperative-code.md)   
 [DynamicActivity 建立](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)