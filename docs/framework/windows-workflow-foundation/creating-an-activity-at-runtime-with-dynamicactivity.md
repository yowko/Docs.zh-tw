---
title: 使用 DynamicActivity 在執行階段建立活動
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321222"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>使用 DynamicActivity 在執行階段建立活動
<xref:System.Activities.DynamicActivity> 是含公用建構函式的具體密封類別。 <xref:System.Activities.DynamicActivity> 可在執行階段中使用活動 DOM 來組合活動功能。  
  
## <a name="dynamicactivity-features"></a>DynamicActivity 功能  
 <xref:System.Activities.DynamicActivity> 可以存取執行屬性、引數和變數，但不可以存取執行階段服務，例如排定子活動或追蹤。  
  
 最上層的屬性可以使用工作流程 <xref:System.Activities.Argument> 物件來設定。 在命令式程式碼中，這些引數是使用新型別的 CLR 屬性建立的。 在 XAML 中，這些引數則是使用 `x:Class` 和 `x:Member` 標籤宣告的。  
  
 使用 <xref:System.Activities.DynamicActivity> 介面建構的活動，此介面具有使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 的設計工具。 在設計工具中建立的活動可使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 動態載入，如下列程序中的示範。  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>若要使用命令式程式碼在執行階段建立活動  
  
1. OpenVisual Studio 2010.  
  
2. 選取 **檔案**，**新**，**專案**。 選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。 選取 **循序工作流程主控台應用程式**中**範本**視窗。 將新專案命名為 DynamicActivitySample。  
  
3. 以滑鼠右鍵按一下 HelloActivity 專案中的 Workflow1.xaml，然後選取**刪除**。  
  
4. 開啟 Program.cs。 將下列指示詞加入至檔案的頂端。  
  
    ```  
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
  
6. 執行應用程式。 含有文字"Hello World ！"的主控台視窗 會顯示。  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>若要使用 XAML 在執行階段建立活動  
  
1. 開啟 Visual Studio 2010。  
  
2. 選取 **檔案**，**新**，**專案**。 選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。 選取 **工作流程主控台應用程式**中**範本**視窗。 將新專案命名為 DynamicActivitySample。  
  
3. 開啟 HelloActivity 專案中的 Workflow1.xaml。 按一下 **引數**底部的設計工具的選項。 建立新的 `In` 引數，其名稱為 `TextToWrite`、型別為 `String`。  
  
4. 拖曳**WriteLine**活動，從**基本型別**拖曳至設計工具介面上的工具箱 的區段。 將值指派`TextToWrite`要**文字**活動的屬性。  
  
5. 開啟 Program.cs。 將下列指示詞加入至檔案的頂端。  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. 以下列程式碼取代 `Main` 方法的內容。  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. 執行應用程式。 含有文字"Hello World ！"的主控台視窗 隨即出現。  
  
8. 以滑鼠右鍵按一下中的 workflow1.xaml**方案總管**，然後選取**檢視程式碼**。 請注意，活動類別是以 `x:Class` 建立的，而屬性則是以 `x:Property` 建立的。  
  
## <a name="see-also"></a>另請參閱

- [使用命令式程式碼撰寫工作流程、活動與運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)
