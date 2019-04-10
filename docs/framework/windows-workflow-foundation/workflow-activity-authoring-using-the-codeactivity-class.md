---
title: 使用 CodeActivity 類別撰寫工作流程活動
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331282"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="02c50-102">使用 CodeActivity 類別撰寫工作流程活動</span><span class="sxs-lookup"><span data-stu-id="02c50-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="02c50-103">繼承自 <xref:System.Activities.CodeActivity> 所建立的活動可藉由覆寫 <xref:System.Activities.CodeActivity.Execute%2A> 方法來實作基本命令式行為。</span><span class="sxs-lookup"><span data-stu-id="02c50-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="02c50-104">使用 CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="02c50-104">Using CodeActivityContext</span></span>
 <span data-ttu-id="02c50-105">工作流程執行階段的功能可透過 <xref:System.Activities.CodeActivity.Execute%2A> 方法內部存取，方法是使用 `context` 參數的成員 (型別為 <xref:System.Activities.CodeActivityContext>)。</span><span class="sxs-lookup"><span data-stu-id="02c50-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="02c50-106">透過 <xref:System.Activities.CodeActivityContext> 可使用的功能如下：</span><span class="sxs-lookup"><span data-stu-id="02c50-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

-   <span data-ttu-id="02c50-107">取得與設定引數和變數的值。</span><span class="sxs-lookup"><span data-stu-id="02c50-107">Getting and setting the values of variables and arguments.</span></span>

-   <span data-ttu-id="02c50-108">使用 <xref:System.Activities.CodeActivityContext.Track%2A> 自訂追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="02c50-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

-   <span data-ttu-id="02c50-109">使用 <xref:System.Activities.CodeActivityContext.GetProperty%2A> 存取活動的執行屬性。</span><span class="sxs-lookup"><span data-stu-id="02c50-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="02c50-110">若要建立繼承自 CodeActivity 的自訂活動</span><span class="sxs-lookup"><span data-stu-id="02c50-110">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="02c50-111">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="02c50-111">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="02c50-112">選取 **檔案**，**新**，然後**專案**。</span><span class="sxs-lookup"><span data-stu-id="02c50-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="02c50-113">選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。</span><span class="sxs-lookup"><span data-stu-id="02c50-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="02c50-114">選取 **活動程式庫**中**範本**視窗。</span><span class="sxs-lookup"><span data-stu-id="02c50-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="02c50-115">將新專案命名為 HelloActivity。</span><span class="sxs-lookup"><span data-stu-id="02c50-115">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="02c50-116">以滑鼠右鍵按一下 HelloActivity 專案中的 Activity1.xaml，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="02c50-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="02c50-117">以滑鼠右鍵按一下 HelloActivity 專案並選取**新增**，然後**類別**。</span><span class="sxs-lookup"><span data-stu-id="02c50-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="02c50-118">將新類別命名為 HelloActivity.cs。</span><span class="sxs-lookup"><span data-stu-id="02c50-118">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="02c50-119">在 HelloActivity.cs 檔案中加入下列 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="02c50-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="02c50-120">將基底類別加入至類別宣告，使新的類別繼承自 <xref:System.Activities.CodeActivity>。</span><span class="sxs-lookup"><span data-stu-id="02c50-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="02c50-121">加入 <xref:System.Activities.CodeActivity.Execute%2A> 方法，藉此將功能加入至類別中。</span><span class="sxs-lookup"><span data-stu-id="02c50-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="02c50-122">使用 <xref:System.Activities.CodeActivityContext> 建立追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="02c50-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
