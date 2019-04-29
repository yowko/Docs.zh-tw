---
title: 逐步解說：自動將自訂元件填入工具箱
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 6ecf69350b8337dc6049b73251809192b47dc2fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759904"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="aacca-102">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="aacca-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="aacca-103">如果您的元件會定義目前開啟的方案中的專案，它們會自動顯示，在**工具箱**，您需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="aacca-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="aacca-104">您可以手動填入**工具箱**以使用您自訂元件[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))，但**工具箱**考慮您的方案中的項目建置輸出具有所有下列特性：</span><span class="sxs-lookup"><span data-stu-id="aacca-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
- <span data-ttu-id="aacca-105">實作<xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="aacca-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
- <span data-ttu-id="aacca-106">沒有<xref:System.ComponentModel.ToolboxItemAttribute>設定為`false`;</span><span class="sxs-lookup"><span data-stu-id="aacca-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
- <span data-ttu-id="aacca-107">沒有<xref:System.ComponentModel.DesignTimeVisibleAttribute>設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="aacca-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aacca-108">**工具箱**並未遵循參考鏈結，所以它不會顯示由您方案中的專案未建置的項目。</span><span class="sxs-lookup"><span data-stu-id="aacca-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="aacca-109">本逐步解說示範如何自訂元件會自動出現在**工具箱**建立元件之後。</span><span class="sxs-lookup"><span data-stu-id="aacca-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="aacca-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="aacca-110">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="aacca-111">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-111">Creating a Windows Forms project.</span></span>  
  
- <span data-ttu-id="aacca-112">建立自訂元件。</span><span class="sxs-lookup"><span data-stu-id="aacca-112">Creating a custom component.</span></span>  
  
- <span data-ttu-id="aacca-113">建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="aacca-113">Creating an instance of a custom component.</span></span>  
  
- <span data-ttu-id="aacca-114">卸載並重新載入自訂元件。</span><span class="sxs-lookup"><span data-stu-id="aacca-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="aacca-115">當您完成時，您會看到**工具箱**會填入您所建立的元件。</span><span class="sxs-lookup"><span data-stu-id="aacca-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aacca-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="aacca-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aacca-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="aacca-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aacca-118">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="aacca-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="aacca-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="aacca-119">Creating the Project</span></span>  
 <span data-ttu-id="aacca-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="aacca-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="aacca-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="aacca-121">To create the project</span></span>  
  
1. <span data-ttu-id="aacca-122">建立以 Windows 為基礎的應用程式專案，稱為`ToolboxExample`(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="aacca-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="aacca-123">將新元件加入至專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-123">Add a new component to the project.</span></span> <span data-ttu-id="aacca-124">稱為 `DemoComponent`。</span><span class="sxs-lookup"><span data-stu-id="aacca-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="aacca-125">如需詳細資訊，請參閱[如何：加入新的專案項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="aacca-125">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="aacca-126">建置專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-126">Build the project.</span></span>  
  
4. <span data-ttu-id="aacca-127">從**工具**功能表上，按一下**選項**項目。</span><span class="sxs-lookup"><span data-stu-id="aacca-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="aacca-128">按一下**一般**下方**Windows Form 設計工具**項目，並確定**AutoToolboxPopulate**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="aacca-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="aacca-129">建立自訂元件的執行個體</span><span class="sxs-lookup"><span data-stu-id="aacca-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="aacca-130">下一個步驟是在表單上建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="aacca-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="aacca-131">因為**工具箱**自動帳戶的新元件，這非常簡單，只要建立其他元件或控制項。</span><span class="sxs-lookup"><span data-stu-id="aacca-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="aacca-132">若要建立自訂元件的執行個體</span><span class="sxs-lookup"><span data-stu-id="aacca-132">To create an instance of a custom component</span></span>  
  
1. <span data-ttu-id="aacca-133">開啟專案的表單**Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="aacca-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2. <span data-ttu-id="aacca-134">在 **工具箱**，按一下 新索引標籤上，並呼叫**ToolboxExample 元件**。</span><span class="sxs-lookup"><span data-stu-id="aacca-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="aacca-135">一旦您按一下  索引標籤，您會看到**DemoComponent**。</span><span class="sxs-lookup"><span data-stu-id="aacca-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aacca-136">基於效能考量，自動填入的區域中的元件**工具箱**不會顯示自訂點陣圖，而<xref:System.Drawing.ToolboxBitmapAttribute>不支援。</span><span class="sxs-lookup"><span data-stu-id="aacca-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="aacca-137">若要顯示的圖示中的自訂元件**工具箱**，使用**選擇工具箱項目**載入您的元件 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aacca-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3. <span data-ttu-id="aacca-138">將您的元件拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="aacca-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="aacca-139">建立並加入至元件的執行個體**元件匣**。</span><span class="sxs-lookup"><span data-stu-id="aacca-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="aacca-140">卸載並重新載入自訂元件</span><span class="sxs-lookup"><span data-stu-id="aacca-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="aacca-141">**工具箱**會考慮在每個元件的載入專案，並卸載專案時，它會移除專案的元件的參考。</span><span class="sxs-lookup"><span data-stu-id="aacca-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="aacca-142">嘗試卸載及重新載入元件的 [工具箱] 上的效果</span><span class="sxs-lookup"><span data-stu-id="aacca-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1. <span data-ttu-id="aacca-143">卸載方案中的專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="aacca-144">如需 卸載專案的詳細資訊，請參閱[How to:卸載並重新載入專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="aacca-144">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="aacca-145">如果提示您儲存時，請選擇**是**。</span><span class="sxs-lookup"><span data-stu-id="aacca-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2. <span data-ttu-id="aacca-146">加入新**Windows 應用程式**專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="aacca-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="aacca-147">開啟中的表單**設計工具**。</span><span class="sxs-lookup"><span data-stu-id="aacca-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="aacca-148">**ToolboxExample 元件**現已從先前的專案 索引標籤不見了。</span><span class="sxs-lookup"><span data-stu-id="aacca-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3. <span data-ttu-id="aacca-149">重新載入`ToolboxExample`專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="aacca-150">**ToolboxExample 元件**索引標籤現在隨即再度出現。</span><span class="sxs-lookup"><span data-stu-id="aacca-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aacca-151">後續步驟</span><span class="sxs-lookup"><span data-stu-id="aacca-151">Next Steps</span></span>  
 <span data-ttu-id="aacca-152">本逐步解說示範**工具箱**考慮專案的元件，但**工具箱**也是會考慮控制項。</span><span class="sxs-lookup"><span data-stu-id="aacca-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="aacca-153">若要試驗您自己的自訂控制項，可新增和移除您的方案中的控制項專案。</span><span class="sxs-lookup"><span data-stu-id="aacca-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aacca-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aacca-154">See also</span></span>

- <span data-ttu-id="aacca-155">[選項對話方塊、 Windows Form 設計工具、 一般](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aacca-155">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="aacca-156">[如何：Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100)) (如何：操作工具箱索引標籤)</span><span class="sxs-lookup"><span data-stu-id="aacca-156">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="aacca-157">[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aacca-157">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="aacca-158">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aacca-158">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
