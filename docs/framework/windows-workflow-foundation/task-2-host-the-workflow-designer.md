---
title: 工作 2：裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 3f7964e907fe513679e60c18292f07c84128590b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299263"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="a9c7b-102">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="a9c7b-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="a9c7b-103">本主題說明的程序裝載的執行個體[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]Windows Presentation Foundation (WPF) 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="a9c7b-104">程序會設定**方格**控制項，其中包含設計工具中，以程式設計方式建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，其中包含預設<xref:System.Activities.Statements.Sequence>活動，會註冊提供的設計工具中繼資料設計工具支援所有內建活動和主機[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]在[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="a9c7b-105">若要裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="a9c7b-105">To host the workflow designer</span></span>  
  
1. <span data-ttu-id="a9c7b-106">開啟的 HostingApplication 專案中建立[工作 1:建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>  
  
2. <span data-ttu-id="a9c7b-107">將視窗調整至方便使用 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 的大小。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="a9c7b-108">若要這樣做，請選取**MainWindow**在設計師中，按 F4 顯示**屬性**視窗中，然後在**配置**那里區段中，將**寬度**值為 600，**高度**350 的值。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3. <span data-ttu-id="a9c7b-109">選取以設定資料格的名稱**格線**設計工具中的面板 (按一下 [] 內的方塊**MainWindow**) 和設定**名稱**頂端的屬性**屬性**為"grid1"視窗。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4. <span data-ttu-id="a9c7b-110">在 **屬性** 視窗中，按一下省略符號 (**...**) 旁`ColumnDefinitions`屬性可開啟**集合編輯器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5. <span data-ttu-id="a9c7b-111">在 [**集合編輯器**] 對話方塊中，按一下**新增**按鈕三次，以插入版面配置中的三個資料行。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="a9c7b-112">第一個資料行會包含**工具箱**，第二個資料行將裝載[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]，以及第三個資料行用於屬性偵測器。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6. <span data-ttu-id="a9c7b-113">設定`Width`屬性中間的資料行的值"4 \*"。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7. <span data-ttu-id="a9c7b-114">按一下 [確定]  儲存變更。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="a9c7b-115">以下的 XAML 已加入至您的 MainWindow.xaml 檔案：</span><span class="sxs-lookup"><span data-stu-id="a9c7b-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8. <span data-ttu-id="a9c7b-116">在 **方案總管**，以滑鼠右鍵按一下 MainWindow.xaml，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="a9c7b-117">遵循下列步驟修改程式碼：</span><span class="sxs-lookup"><span data-stu-id="a9c7b-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="a9c7b-118">加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="a9c7b-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="a9c7b-119">若要宣告私用成員欄位以保留 <xref:System.Activities.Presentation.WorkflowDesigner> 的執行個體，請將下列程式碼加入至 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
        ```csharp  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
        ```  
  
    3.  <span data-ttu-id="a9c7b-120">將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="a9c7b-121">這個實作會建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，將<xref:System.Activities.Statements.Sequence>活動，並將它放在中間的資料行的 grid1**格線**。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
        ```csharp  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
        ```  
  
    4.  <span data-ttu-id="a9c7b-122">註冊設計工具中繼資料，為所有內建活動加入設計工具支援。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="a9c7b-123">這樣可讓您從工具箱將活動放置於 <xref:System.Activities.Statements.Sequence> 中的原始 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 活動。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="a9c7b-124">若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="a9c7b-125">如需有關如何註冊活動設計工具的詳細資訊，請參閱[How to:建立自訂活動設計工具](how-to-create-a-custom-activity-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="a9c7b-126">在 `MainWindow` 類別建構函式中，將呼叫加入至先前宣告的方法，為中繼資料註冊設計工具支援，以建立 <xref:System.Activities.Presentation.WorkflowDesigner>。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="a9c7b-127">`RegisterMetadata` 方法會註冊內建活動 (包括 <xref:System.Activities.Statements.Sequence> 活動) 的設計工具中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="a9c7b-128">由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="a9c7b-129">按 F5 以建置及執行方案。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="a9c7b-130">請參閱[工作 3:建立工具箱與 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)以了解如何新增**工具箱**並**PropertyGrid**支援新增至您的重新裝載工作流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="a9c7b-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c7b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c7b-131">See also</span></span>

- [<span data-ttu-id="a9c7b-132">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="a9c7b-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="a9c7b-133">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="a9c7b-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="a9c7b-134">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="a9c7b-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
