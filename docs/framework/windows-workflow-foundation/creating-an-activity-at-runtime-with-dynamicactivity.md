---
title: 使用 DynamicActivity 在執行階段建立活動
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182984"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>使用 DynamicActivity 在執行階段建立活動
<xref:System.Activities.DynamicActivity> 是含公用建構函式的具體密封類別。 <xref:System.Activities.DynamicActivity> 可在執行階段中使用活動 DOM 來組合活動功能。  
  
## <a name="dynamicactivity-features"></a>DynamicActivity 功能  
 <xref:System.Activities.DynamicActivity> 可以存取執行屬性、引數和變數，但不可以存取執行階段服務，例如排定子活動或追蹤。  
  
 最上層的屬性可以使用工作流程 <xref:System.Activities.Argument> 物件來設定。 在命令式程式碼中，這些引數是使用新型別的 CLR 屬性建立的。 在 XAML 中，這些引數則是使用 `x:Class` 和 `x:Member` 標籤宣告的。  
  
 使用 <xref:System.Activities.DynamicActivity> 介面建構的活動，此介面具有使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 的設計工具。 在設計工具中建立的活動可使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 動態載入，如下列程序中的示範。  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>若要使用命令式程式碼在執行階段建立活動  
  
1. 開放視覺工作室 2010.  
  
2. 選擇**檔**，**新建**，**專案**. 在 **"專案類型"** 視窗中的 **"視覺化 C#"** 下選擇**工作流 4.0，** 然後選擇**v2010**節點。 在**範本**視窗中選擇**順序工作流主控台應用程式**。 將新專案命名為 DynamicActivitySample。  
  
3. 按右鍵 HelloActivity 專案中的工作流1.xaml，然後選擇 **"刪除**"。  
  
4. 開啟 Program.cs。 將下列指示詞加入至檔案的頂端。  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. 以下列程式碼取代 `Main` 方法的內容，此程式碼會建立 <xref:System.Activities.Statements.Sequence> 活動 (包含單一 <xref:System.Activities.Statements.WriteLine> 活動)，並將該活動指派至新的動態活動之 <xref:System.Activities.DynamicActivity.Implementation%2A> 屬性。  
  
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
  
6. 執行應用程式。 主控台視窗，上面寫著"你好世界！ 顯示。  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>若要使用 XAML 在執行階段建立活動  
  
1. 開啟 Visual Studio 2010。  
  
2. 選擇**檔**，**新建**，**專案**. 在 **"專案類型"** 視窗中的 **"視覺化 C#"** 下選擇**工作流 4.0，** 然後選擇**v2010**節點。 在**範本**視窗中選擇**工作流主控台應用程式**。 將新專案命名為 DynamicActivitySample。  
  
3. 開啟 HelloActivity 專案中的 Workflow1.xaml。 按一下設計器底部的 **"參數"** 選項。 建立新的 `In` 引數，其名稱為 `TextToWrite`、型別為 `String`。  
  
4. 將 **"寫入線"** 活動從工具箱的 **"原始"** 部分拖動到設計器曲面上。 將值`TextToWrite`分配給活動的**Text**屬性。  
  
5. 開啟 Program.cs。 將下列指示詞加入至檔案的頂端。  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. 以下列程式碼取代 `Main` 方法的內容。  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. 執行應用程式。 主控台視窗，上面寫著"你好世界！  隨即出現。  
  
8. 按右鍵**解決方案資源管理器**中的 Workflow1.xaml 檔，然後選擇 **"查看代碼**"。 請注意，活動類別是以 `x:Class` 建立的，而屬性則是以 `x:Property` 建立的。  
  
## <a name="see-also"></a>另請參閱

- [使用命令式程式碼撰寫工作流程、活動與運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)
