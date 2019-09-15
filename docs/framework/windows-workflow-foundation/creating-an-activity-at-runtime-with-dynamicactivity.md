---
title: 使用 DynamicActivity 在執行階段建立活動
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: de67fdd71f28bc0f4b16017d253682ca2615f854
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989732"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="b8d8a-102">使用 DynamicActivity 在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="b8d8a-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="b8d8a-103"><xref:System.Activities.DynamicActivity> 是含公用建構函式的具體密封類別。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="b8d8a-104"><xref:System.Activities.DynamicActivity> 可在執行階段中使用活動 DOM 來組合活動功能。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="b8d8a-105">DynamicActivity 功能</span><span class="sxs-lookup"><span data-stu-id="b8d8a-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="b8d8a-106"><xref:System.Activities.DynamicActivity> 可以存取執行屬性、引數和變數，但不可以存取執行階段服務，例如排定子活動或追蹤。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="b8d8a-107">最上層的屬性可以使用工作流程 <xref:System.Activities.Argument> 物件來設定。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="b8d8a-108">在命令式程式碼中，這些引數是使用新型別的 CLR 屬性建立的。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="b8d8a-109">在 XAML 中，這些引數則是使用 `x:Class` 和 `x:Member` 標籤宣告的。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="b8d8a-110">使用 <xref:System.Activities.DynamicActivity> 介面建構的活動，此介面具有使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 的設計工具。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="b8d8a-111">在設計工具中建立的活動可使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 動態載入，如下列程序中的示範。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="b8d8a-112">若要使用命令式程式碼在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="b8d8a-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="b8d8a-113">OpenVisual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="b8d8a-114">選取 [檔案]、[**新增** **]、[** **專案**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="b8d8a-115">在 **專案類型** 視窗中，選取 **視覺效果C#**   底下的  **Workflow 4.0** ，然後選取  **v2010**  節點</span><span class="sxs-lookup"><span data-stu-id="b8d8a-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="b8d8a-116">在 [**範本**] 視窗中選取 [**連續工作流程主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="b8d8a-117">將新專案命名為 DynamicActivitySample。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="b8d8a-118">以滑鼠右鍵按一下 HelloActivity 專案中的 Workflow1.xaml，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="b8d8a-119">開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-119">Open Program.cs.</span></span> <span data-ttu-id="b8d8a-120">將下列指示詞加入至檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="b8d8a-121">以下列程式碼取代 `Main` 方法的內容，此程式碼會建立 <xref:System.Activities.Statements.Sequence> 活動 (包含單一 <xref:System.Activities.Statements.WriteLine> 活動)，並將該活動指派至新的動態活動之 <xref:System.Activities.DynamicActivity.Implementation%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="b8d8a-122">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-122">Execute the application.</span></span> <span data-ttu-id="b8d8a-123">含有 "Hello World！" 文字的主控台視窗</span><span class="sxs-lookup"><span data-stu-id="b8d8a-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="b8d8a-124">出現.</span><span class="sxs-lookup"><span data-stu-id="b8d8a-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="b8d8a-125">若要使用 XAML 在執行階段建立活動</span><span class="sxs-lookup"><span data-stu-id="b8d8a-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="b8d8a-126">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="b8d8a-127">選取 [檔案]、[**新增** **]、[** **專案**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="b8d8a-128">在 **專案類型** 視窗中，選取 **視覺效果C#**   底下的  **Workflow 4.0** ，然後選取  **v2010**  節點</span><span class="sxs-lookup"><span data-stu-id="b8d8a-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="b8d8a-129">在 [**範本**] 視窗中選取 [**工作流程主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="b8d8a-130">將新專案命名為 DynamicActivitySample。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="b8d8a-131">開啟 HelloActivity 專案中的 Workflow1.xaml。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="b8d8a-132">按一下設計工具底部的 [**引數**] 選項。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="b8d8a-133">建立新的 `In` 引數，其名稱為 `TextToWrite`、型別為 `String`。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="b8d8a-134">將 [ **WriteLine** ] 活動從 [工具箱] 的 [**基本**] 區段拖曳到設計工具介面上。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="b8d8a-135">將值`TextToWrite`指派給活動的**Text**屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="b8d8a-136">開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-136">Open Program.cs.</span></span> <span data-ttu-id="b8d8a-137">將下列指示詞加入至檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="b8d8a-138">以下列程式碼取代 `Main` 方法的內容。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="b8d8a-139">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-139">Execute the application.</span></span> <span data-ttu-id="b8d8a-140">含有 "Hello World！" 文字的主控台視窗</span><span class="sxs-lookup"><span data-stu-id="b8d8a-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="b8d8a-141">看.</span><span class="sxs-lookup"><span data-stu-id="b8d8a-141">appears.</span></span>  
  
8. <span data-ttu-id="b8d8a-142">以滑鼠右鍵按一下**方案總管**中的 workflow1.xaml，然後選取 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="b8d8a-143">請注意，活動類別是以 `x:Class` 建立的，而屬性則是以 `x:Property` 建立的。</span><span class="sxs-lookup"><span data-stu-id="b8d8a-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d8a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d8a-144">See also</span></span>

- [<span data-ttu-id="b8d8a-145">使用命令式程式碼撰寫工作流程、活動與運算式</span><span class="sxs-lookup"><span data-stu-id="b8d8a-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
