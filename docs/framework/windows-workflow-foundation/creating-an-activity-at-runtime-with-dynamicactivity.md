---
title: 使用 DynamicActivity 在執行階段建立活動
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321222"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="734c5-102">使用 DynamicActivity 在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="734c5-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<xref:System.Activities.DynamicActivity> <span data-ttu-id="734c5-103">是具體、 密封的類別具有公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="734c5-103">is a concrete, sealed class with a public constructor.</span></span> <xref:System.Activities.DynamicActivity> <span data-ttu-id="734c5-104">可用來組合活動功能，在執行階段使用活動 dom。</span><span class="sxs-lookup"><span data-stu-id="734c5-104">can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="734c5-105">DynamicActivity 功能</span><span class="sxs-lookup"><span data-stu-id="734c5-105">DynamicActivity Features</span></span>  
 <xref:System.Activities.DynamicActivity> <span data-ttu-id="734c5-106">具有存取執行屬性、 引數和變數，但不是能存取執行階段服務，例如排程子活動或追蹤。</span><span class="sxs-lookup"><span data-stu-id="734c5-106">has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="734c5-107">最上層的屬性可以使用工作流程 <xref:System.Activities.Argument> 物件來設定。</span><span class="sxs-lookup"><span data-stu-id="734c5-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="734c5-108">在命令式程式碼中，這些引數是使用新型別的 CLR 屬性建立的。</span><span class="sxs-lookup"><span data-stu-id="734c5-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="734c5-109">在 XAML 中，這些引數則是使用 `x:Class` 和 `x:Member` 標籤宣告的。</span><span class="sxs-lookup"><span data-stu-id="734c5-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="734c5-110">使用 <xref:System.Activities.DynamicActivity> 介面建構的活動，此介面具有使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 的設計工具。</span><span class="sxs-lookup"><span data-stu-id="734c5-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="734c5-111">在設計工具中建立的活動可使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 動態載入，如下列程序中的示範。</span><span class="sxs-lookup"><span data-stu-id="734c5-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="734c5-112">若要使用命令式程式碼在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="734c5-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="734c5-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="734c5-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="734c5-114">選取 **檔案**，**新**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="734c5-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="734c5-115">選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。</span><span class="sxs-lookup"><span data-stu-id="734c5-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="734c5-116">選取 **循序工作流程主控台應用程式**中**範本**視窗。</span><span class="sxs-lookup"><span data-stu-id="734c5-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="734c5-117">將新專案命名為 DynamicActivitySample。</span><span class="sxs-lookup"><span data-stu-id="734c5-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="734c5-118">以滑鼠右鍵按一下 HelloActivity 專案中的 Workflow1.xaml，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="734c5-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="734c5-119">開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="734c5-119">Open Program.cs.</span></span> <span data-ttu-id="734c5-120">將下列指示詞加入至檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="734c5-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="734c5-121">以下列程式碼取代 `Main` 方法的內容，此程式碼會建立 <xref:System.Activities.Statements.Sequence> 活動 (包含單一 <xref:System.Activities.Statements.WriteLine> 活動)，並將該活動指派至新的動態活動之 <xref:System.Activities.DynamicActivity.Implementation%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="734c5-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="734c5-122">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="734c5-122">Execute the application.</span></span> <span data-ttu-id="734c5-123">含有文字"Hello World ！"的主控台視窗</span><span class="sxs-lookup"><span data-stu-id="734c5-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="734c5-124">會顯示。</span><span class="sxs-lookup"><span data-stu-id="734c5-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="734c5-125">若要使用 XAML 在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="734c5-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="734c5-126">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="734c5-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="734c5-127">選取 **檔案**，**新**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="734c5-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="734c5-128">選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。</span><span class="sxs-lookup"><span data-stu-id="734c5-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="734c5-129">選取 **工作流程主控台應用程式**中**範本**視窗。</span><span class="sxs-lookup"><span data-stu-id="734c5-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="734c5-130">將新專案命名為 DynamicActivitySample。</span><span class="sxs-lookup"><span data-stu-id="734c5-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="734c5-131">開啟 HelloActivity 專案中的 Workflow1.xaml。</span><span class="sxs-lookup"><span data-stu-id="734c5-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="734c5-132">按一下 **引數**底部的設計工具的選項。</span><span class="sxs-lookup"><span data-stu-id="734c5-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="734c5-133">建立新的 `In` 引數，其名稱為 `TextToWrite`、型別為 `String`。</span><span class="sxs-lookup"><span data-stu-id="734c5-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="734c5-134">拖曳**WriteLine**活動，從**基本型別**拖曳至設計工具介面上的工具箱 的區段。</span><span class="sxs-lookup"><span data-stu-id="734c5-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="734c5-135">將值指派`TextToWrite`要**文字**活動的屬性。</span><span class="sxs-lookup"><span data-stu-id="734c5-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="734c5-136">開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="734c5-136">Open Program.cs.</span></span> <span data-ttu-id="734c5-137">將下列指示詞加入至檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="734c5-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="734c5-138">以下列程式碼取代 `Main` 方法的內容。</span><span class="sxs-lookup"><span data-stu-id="734c5-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="734c5-139">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="734c5-139">Execute the application.</span></span> <span data-ttu-id="734c5-140">含有文字"Hello World ！"的主控台視窗</span><span class="sxs-lookup"><span data-stu-id="734c5-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="734c5-141">隨即出現。</span><span class="sxs-lookup"><span data-stu-id="734c5-141">appears.</span></span>  
  
8. <span data-ttu-id="734c5-142">以滑鼠右鍵按一下中的 workflow1.xaml**方案總管**，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="734c5-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="734c5-143">請注意，活動類別是以 `x:Class` 建立的，而屬性則是以 `x:Property` 建立的。</span><span class="sxs-lookup"><span data-stu-id="734c5-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734c5-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="734c5-144">See also</span></span>

- [<span data-ttu-id="734c5-145">使用命令式程式碼撰寫工作流程、活動和運算式</span><span class="sxs-lookup"><span data-stu-id="734c5-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
