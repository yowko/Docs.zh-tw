---
title: 逐步解說：自動將自訂元件填入工具箱
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211151"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="a3cd8-102">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="a3cd8-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>

<span data-ttu-id="a3cd8-103">如果您的元件會定義目前開啟的方案中的專案，它們會自動顯示，在**工具箱**，您需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="a3cd8-104">您可以手動填入**工具箱**以使用您自訂元件[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))，但**工具箱**考慮您的方案中的項目建置輸出具有所有下列特性：</span><span class="sxs-lookup"><span data-stu-id="a3cd8-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>

- <span data-ttu-id="a3cd8-105">實作<xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="a3cd8-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>

- <span data-ttu-id="a3cd8-106">沒有<xref:System.ComponentModel.ToolboxItemAttribute>設定為`false`;</span><span class="sxs-lookup"><span data-stu-id="a3cd8-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>

- <span data-ttu-id="a3cd8-107">沒有<xref:System.ComponentModel.DesignTimeVisibleAttribute>設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="a3cd8-108">**工具箱**並未遵循參考鏈結，所以它不會顯示由您方案中的專案未建置的項目。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-108">The **Toolbox** does not follow reference chains, so it won't display items that are not built by a project in your solution.</span></span>

<span data-ttu-id="a3cd8-109">本逐步解說示範如何自訂元件會自動出現在**工具箱**建立元件之後。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="a3cd8-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a3cd8-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="a3cd8-111">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-111">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="a3cd8-112">建立自訂元件。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-112">Creating a custom component.</span></span>

- <span data-ttu-id="a3cd8-113">建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-113">Creating an instance of a custom component.</span></span>

- <span data-ttu-id="a3cd8-114">卸載並重新載入自訂元件。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-114">Unloading and reloading a custom component.</span></span>

<span data-ttu-id="a3cd8-115">當您完成時，您會看到**工具箱**會填入您所建立的元件。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a3cd8-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="a3cd8-116">Create the project</span></span>

1. <span data-ttu-id="a3cd8-117">在 Visual Studio 中建立名為以 Windows 為基礎的應用程式專案`ToolboxExample`(**檔案** > **新增** > **專案** > **視覺化C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-117">In Visual Studio, create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="a3cd8-118">將新元件加入至專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-118">Add a new component to the project.</span></span> <span data-ttu-id="a3cd8-119">稱為 `DemoComponent`。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-119">Call it `DemoComponent`.</span></span>

     <span data-ttu-id="a3cd8-120">如需詳細資訊，請參閱[如何：加入新的專案項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-120">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>

3. <span data-ttu-id="a3cd8-121">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-121">Build the project.</span></span>

4. <span data-ttu-id="a3cd8-122">從**工具**功能表上，按一下**選項**項目。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-122">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="a3cd8-123">按一下**一般**下方**Windows Form 設計工具**項目，並確定**AutoToolboxPopulate**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-123">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>

## <a name="create-an-instance-of-a-custom-component"></a><span data-ttu-id="a3cd8-124">建立自訂元件的執行個體</span><span class="sxs-lookup"><span data-stu-id="a3cd8-124">Create an instance of a custom component</span></span>

<span data-ttu-id="a3cd8-125">下一個步驟是在表單上建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-125">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="a3cd8-126">因為**工具箱**自動帳戶的新元件，這非常簡單，只要建立其他元件或控制項。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-126">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>

1. <span data-ttu-id="a3cd8-127">開啟專案的表單**Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-127">Open the project's form in the **Forms Designer**.</span></span>

2. <span data-ttu-id="a3cd8-128">在 **工具箱**，按一下 新索引標籤上，並呼叫**ToolboxExample 元件**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-128">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>

     <span data-ttu-id="a3cd8-129">一旦您按一下  索引標籤，您會看到**DemoComponent**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-129">Once you click the tab, you will see **DemoComponent**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a3cd8-130">基於效能考量，自動填入的區域中的元件**工具箱**不會顯示自訂點陣圖，而<xref:System.Drawing.ToolboxBitmapAttribute>不支援。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-130">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="a3cd8-131">若要顯示的圖示中的自訂元件**工具箱**，使用**選擇工具箱項目**載入您的元件 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-131">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>

3. <span data-ttu-id="a3cd8-132">將您的元件拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-132">Drag your component onto your form.</span></span>

     <span data-ttu-id="a3cd8-133">建立並加入至元件的執行個體**元件匣**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-133">An instance of the component is created and added to the **Component Tray**.</span></span>

## <a name="unload-and-reload-a-custom-component"></a><span data-ttu-id="a3cd8-134">卸載並重新載入自訂元件</span><span class="sxs-lookup"><span data-stu-id="a3cd8-134">Unload and reload a custom component</span></span>

<span data-ttu-id="a3cd8-135">**工具箱**會考慮在每個元件的載入專案，並卸載專案時，它會移除專案的元件的參考。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-135">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>

1. <span data-ttu-id="a3cd8-136">卸載方案中的專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-136">Unload the project from the solution.</span></span>

     <span data-ttu-id="a3cd8-137">如需 卸載專案的詳細資訊，請參閱[How to:卸載並重新載入專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-137">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="a3cd8-138">如果提示您儲存時，請選擇**是**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-138">If you are prompted to save, choose **Yes**.</span></span>

2. <span data-ttu-id="a3cd8-139">加入新**Windows 應用程式**專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-139">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="a3cd8-140">開啟中的表單**設計工具**。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-140">Open the form in the **Designer**.</span></span>

     <span data-ttu-id="a3cd8-141">**ToolboxExample 元件**現已從先前的專案 索引標籤不見了。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-141">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>

3. <span data-ttu-id="a3cd8-142">重新載入`ToolboxExample`專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-142">Reload the `ToolboxExample` project.</span></span>

     <span data-ttu-id="a3cd8-143">**ToolboxExample 元件**索引標籤現在隨即再度出現。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-143">The **ToolboxExample Components** tab now reappears.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3cd8-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a3cd8-144">Next steps</span></span>

<span data-ttu-id="a3cd8-145">本逐步解說示範**工具箱**考慮專案的元件，但**工具箱**也是會考慮控制項。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-145">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="a3cd8-146">若要試驗您自己的自訂控制項，可新增和移除您的方案中的控制項專案。</span><span class="sxs-lookup"><span data-stu-id="a3cd8-146">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3cd8-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3cd8-147">See also</span></span>

- <span data-ttu-id="a3cd8-148">[選項對話方塊、 Windows Form 設計工具、 一般](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3cd8-148">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="a3cd8-149">[如何：Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100)) (如何：操作工具箱索引標籤)</span><span class="sxs-lookup"><span data-stu-id="a3cd8-149">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="a3cd8-150">[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3cd8-150">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="a3cd8-151">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3cd8-151">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
