---
title: "逐步解說：自動將自訂元件填入工具箱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 691487046e2a34dbf233dc4bc03e20f9ec245da1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="32761-102">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="32761-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="32761-103">如果您的元件會由目前開啟的方案中的專案，會自動將會出現在**工具箱**，而不需要您所需的動作。</span><span class="sxs-lookup"><span data-stu-id="32761-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="32761-104">您也可以手動填入**工具箱**與使用自訂元件[選擇工具箱項目 對話方塊 (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)，但**工具箱**考慮您的方案中的項目建置輸出具有所有下列特性：</span><span class="sxs-lookup"><span data-stu-id="32761-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="32761-105">實作<xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="32761-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="32761-106">沒有<xref:System.ComponentModel.ToolboxItemAttribute>設`false`;</span><span class="sxs-lookup"><span data-stu-id="32761-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="32761-107">沒有<xref:System.ComponentModel.DesignTimeVisibleAttribute>設`false`。</span><span class="sxs-lookup"><span data-stu-id="32761-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32761-108">**工具箱**未遵循參考鏈結，所以它不會顯示並不是您方案中的專案所建置的項目。</span><span class="sxs-lookup"><span data-stu-id="32761-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="32761-109">本逐步解說示範如何自訂元件會自動出現在**工具箱**建置元件之後。</span><span class="sxs-lookup"><span data-stu-id="32761-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="32761-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="32761-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="32761-111">建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="32761-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="32761-112">建立自訂元件。</span><span class="sxs-lookup"><span data-stu-id="32761-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="32761-113">建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="32761-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="32761-114">卸載並重新載入自訂元件。</span><span class="sxs-lookup"><span data-stu-id="32761-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="32761-115">當您完成時，您會看到**工具箱**會填入您所建立的元件。</span><span class="sxs-lookup"><span data-stu-id="32761-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32761-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="32761-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="32761-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="32761-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="32761-118">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="32761-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="32761-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="32761-119">Creating the Project</span></span>  
 <span data-ttu-id="32761-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="32761-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="32761-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="32761-121">To create the project</span></span>  
  
1.  <span data-ttu-id="32761-122">建立以 Windows 為基礎的應用程式專案，名為 `ToolboxExample`。</span><span class="sxs-lookup"><span data-stu-id="32761-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="32761-123">如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="32761-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="32761-124">將新元件加入至專案。</span><span class="sxs-lookup"><span data-stu-id="32761-124">Add a new component to the project.</span></span> <span data-ttu-id="32761-125">呼叫它`DemoComponent`。</span><span class="sxs-lookup"><span data-stu-id="32761-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="32761-126">如需詳細資訊，請參閱[NIB： 如何： 加入新的專案項目](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。</span><span class="sxs-lookup"><span data-stu-id="32761-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="32761-127">建置專案。</span><span class="sxs-lookup"><span data-stu-id="32761-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="32761-128">從**工具**功能表上，按一下 **選項**項目。</span><span class="sxs-lookup"><span data-stu-id="32761-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="32761-129">按一下**一般**下**Windows Form 設計工具**項目，並確定**AutoToolboxPopulate**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="32761-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="32761-130">建立自訂元件的執行個體</span><span class="sxs-lookup"><span data-stu-id="32761-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="32761-131">下一個步驟是在表單上建立自訂元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="32761-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="32761-132">因為**工具箱**自動帳戶的新元件，這非常容易，只要建立元件或控制項。</span><span class="sxs-lookup"><span data-stu-id="32761-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="32761-133">若要建立自訂元件的執行個體</span><span class="sxs-lookup"><span data-stu-id="32761-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="32761-134">開啟專案的表單中**Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="32761-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="32761-135">在**工具箱**，按一下 新索引標籤呼叫**ToolboxExample 元件**。</span><span class="sxs-lookup"><span data-stu-id="32761-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="32761-136">一旦您按一下索引標籤，您會看到**DemoComponent**。</span><span class="sxs-lookup"><span data-stu-id="32761-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32761-137">基於效能考量，自動填入內容區域中的元件**工具箱**不會顯示自訂點陣圖與<xref:System.Drawing.ToolboxBitmapAttribute>不支援。</span><span class="sxs-lookup"><span data-stu-id="32761-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="32761-138">若要顯示的圖示中的自訂元件**工具箱**，使用**選擇工具箱項目**載入您的元件 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="32761-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="32761-139">您的元件拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="32761-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="32761-140">建立元件的執行個體並將其加入**元件匣**。</span><span class="sxs-lookup"><span data-stu-id="32761-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="32761-141">卸載並重新載入自訂元件</span><span class="sxs-lookup"><span data-stu-id="32761-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="32761-142">**工具箱**會考慮在每個元件的載入專案，並卸載專案之後，它會移除專案的元件的參考。</span><span class="sxs-lookup"><span data-stu-id="32761-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="32761-143">若要試驗的卸載和重新載入元件工具箱上的效果</span><span class="sxs-lookup"><span data-stu-id="32761-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="32761-144">專案從方案中卸載。</span><span class="sxs-lookup"><span data-stu-id="32761-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="32761-145">如需 卸載專案的詳細資訊，請參閱[NIB： 如何： 卸載再重新載入專案](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b)。</span><span class="sxs-lookup"><span data-stu-id="32761-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="32761-146">如果提示您儲存時，請選擇**是**。</span><span class="sxs-lookup"><span data-stu-id="32761-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="32761-147">加入新**Windows 應用程式**專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="32761-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="32761-148">開啟表單中的**設計師**。</span><span class="sxs-lookup"><span data-stu-id="32761-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="32761-149">**ToolboxExample 元件**從先前的專案 索引標籤現在會消失。</span><span class="sxs-lookup"><span data-stu-id="32761-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="32761-150">重新載入`ToolboxExample`專案。</span><span class="sxs-lookup"><span data-stu-id="32761-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="32761-151">**ToolboxExample 元件**索引標籤現在隨即再度出現。</span><span class="sxs-lookup"><span data-stu-id="32761-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="32761-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="32761-152">Next Steps</span></span>  
 <span data-ttu-id="32761-153">本逐步解說會示範**工具箱**考慮專案的元件，但**工具箱**也是會考慮控制項。</span><span class="sxs-lookup"><span data-stu-id="32761-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="32761-154">實驗您自己的自訂控制項加入和移除控制項的專案，從您的方案。</span><span class="sxs-lookup"><span data-stu-id="32761-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32761-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32761-155">See Also</span></span>  
 [<span data-ttu-id="32761-156">選項對話方塊、 Windows Form 設計工具，一般</span><span class="sxs-lookup"><span data-stu-id="32761-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="32761-157">如何：操作工具箱索引標籤</span><span class="sxs-lookup"><span data-stu-id="32761-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="32761-158">選擇工具箱項目對話方塊 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="32761-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="32761-159">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32761-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
