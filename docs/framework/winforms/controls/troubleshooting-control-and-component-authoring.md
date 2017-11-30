---
title: "控制項和元件撰寫疑難排解"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="3813d-102">控制項和元件撰寫疑難排解</span><span class="sxs-lookup"><span data-stu-id="3813d-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="3813d-103">本主題列出當開發元件和控制項時，會發生下列常見問題。</span><span class="sxs-lookup"><span data-stu-id="3813d-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="3813d-104">如需詳細資訊，請參閱[使用元件進行程式設計](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)。</span><span class="sxs-lookup"><span data-stu-id="3813d-104">For more information, see [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="3813d-105">無法將控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3813d-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="3813d-106">無法針對 Windows Forms 使用者控制項或元件進行偵錯</span><span class="sxs-lookup"><span data-stu-id="3813d-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="3813d-107">事件在繼承的控制項或元件中引發兩次</span><span class="sxs-lookup"><span data-stu-id="3813d-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="3813d-108">設計階段錯誤：「無法建立元件 '元件名稱'」</span><span class="sxs-lookup"><span data-stu-id="3813d-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="3813d-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="3813d-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="3813d-110">元件圖示不會出現在工具箱中</span><span class="sxs-lookup"><span data-stu-id="3813d-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="3813d-111">無法將控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3813d-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="3813d-112">如果您想要將您在另一個專案中建立的自訂控制項或協力廠商控制項新增至 [工具箱]，您必須手動進行。</span><span class="sxs-lookup"><span data-stu-id="3813d-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="3813d-113">如果目前專案包含您的控制項或元件，它應該會自動出現在 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="3813d-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="3813d-114">如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。</span><span class="sxs-lookup"><span data-stu-id="3813d-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="3813d-115">將控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3813d-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="3813d-116">以滑鼠右鍵按一下 [工具箱]，然後從捷徑功能表選取 [選擇項目]。</span><span class="sxs-lookup"><span data-stu-id="3813d-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="3813d-117">在 [選擇工具箱項目] 對話方塊中，新增元件：</span><span class="sxs-lookup"><span data-stu-id="3813d-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="3813d-118">如果您想要新增 .NET Framework 元件或控制項，請按一下 [.NET Framework 元件] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3813d-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="3813d-119">-或-</span><span class="sxs-lookup"><span data-stu-id="3813d-119">– or –</span></span>  
  
    -   <span data-ttu-id="3813d-120">如果您想要新增 COM 元件或 ActiveX 控制項，請按一下 [COM 元件] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3813d-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="3813d-121">如果您的控制項列在對話方塊中，確認它已選取，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3813d-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3813d-122">控制項隨即新增至 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="3813d-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="3813d-123">如果您的控制項未列在對話方塊中，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="3813d-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3813d-124">按一下 [瀏覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3813d-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="3813d-125">瀏覽至包含 .dll 檔案 (包含您的控制項) 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3813d-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="3813d-126">選取 .dll 檔案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="3813d-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="3813d-127">您的控制項會出現在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="3813d-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="3813d-128">確認已選取您的控制項，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3813d-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="3813d-129">您的控制項隨即新增至 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="3813d-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="3813d-130">無法針對 Windows Forms 使用者控制項或元件進行偵錯</span><span class="sxs-lookup"><span data-stu-id="3813d-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="3813d-131">如果您的控制項衍生自<xref:System.Windows.Forms.UserControl>類別，您可以偵錯與測試容器及其執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="3813d-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="3813d-132">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="3813d-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="3813d-133">其他自訂控制項和元件不是獨立的專案。</span><span class="sxs-lookup"><span data-stu-id="3813d-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="3813d-134">它們必須由 Windows Forms 專案之類的應用程式裝載。</span><span class="sxs-lookup"><span data-stu-id="3813d-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="3813d-135">若要針對控制項或元件進行偵錯，您必須將它新增至 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="3813d-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="3813d-136">針對控制項或元件進行偵錯</span><span class="sxs-lookup"><span data-stu-id="3813d-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="3813d-137">按一下 [建置] 功能表上的 [建置方案] 以建置解決方案。</span><span class="sxs-lookup"><span data-stu-id="3813d-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="3813d-138">從 [檔案]功能表，選擇 [新增]，然後選擇 [新增專案]，以將測試專案新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3813d-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="3813d-139">在 [加入新的專案] 對話方塊中，針對專案型別選擇 [Windows 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="3813d-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="3813d-140">在 [方案總管] 中，以滑鼠右鍵按一下新專案的 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="3813d-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="3813d-141">在捷徑功能表上，按一下 [加入參考]  以將參考新增至包含控制項或元件的專案。</span><span class="sxs-lookup"><span data-stu-id="3813d-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="3813d-142">在測試專案中建立您的控制項或元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3813d-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="3813d-143">如果您的元件位於 [工具箱]，您可以將它拖曳至設計工具介面，或者您可以程式設計方式建立執行個體，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="3813d-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="3813d-144">您現在可以如同往常一般針對您的控制項或元件進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="3813d-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="3813d-145">如需偵錯的詳細資訊，請參閱[在 Visual Studio 中偵錯](/visualstudio/debugger/debugging-in-visual-studio)和[逐步解說︰在設計階段針對自訂 Windows Forms 控制項進行偵錯](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="3813d-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="3813d-146">事件在繼承的控制項或元件中引發兩次</span><span class="sxs-lookup"><span data-stu-id="3813d-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="3813d-147">這可能是因為重複的 `Handles` 子句。</span><span class="sxs-lookup"><span data-stu-id="3813d-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="3813d-148">如需詳細資訊，請參閱 [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="3813d-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="3813d-149">設計階段錯誤：「無法建立元件 '元件名稱'」</span><span class="sxs-lookup"><span data-stu-id="3813d-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="3813d-150">您的元件或控制項必須提供沒有參數的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="3813d-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="3813d-151">當設計環境建立元件或控制項的執行個體時，它不會嘗試提供任何參數給採用參數的建構函式多載。</span><span class="sxs-lookup"><span data-stu-id="3813d-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="3813d-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="3813d-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="3813d-153"><xref:System.STAThreadAttribute>通知 common language runtime (CLR) Windows Form 使用單一執行緒 apartment 模式。</span><span class="sxs-lookup"><span data-stu-id="3813d-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="3813d-154">如果您未將此屬性套用至 Windows Forms 應用程式的 `Main` 方法，您可能會發現非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="3813d-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="3813d-155">例如，背景影像可能不會出現針對類似控制項<xref:System.Windows.Forms.ListView>。</span><span class="sxs-lookup"><span data-stu-id="3813d-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="3813d-156">某些控制項可能也需要此屬性，才能有正確的 AutoComplete 和拖放行為。</span><span class="sxs-lookup"><span data-stu-id="3813d-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="3813d-157">元件圖示不會出現在工具箱中</span><span class="sxs-lookup"><span data-stu-id="3813d-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="3813d-158">當您使用<xref:System.Drawing.ToolboxBitmapAttribute>圖示與您的自訂元件，點陣圖不會自動產生元件的 [工具箱] 中顯示。</span><span class="sxs-lookup"><span data-stu-id="3813d-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="3813d-159">若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。</span><span class="sxs-lookup"><span data-stu-id="3813d-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="3813d-160">如需詳細資訊，請參閱[如何：為控制項提供工具箱點陣圖](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3813d-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3813d-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3813d-161">See Also</span></span>  
 [<span data-ttu-id="3813d-162">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="3813d-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="3813d-163">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="3813d-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="3813d-164">操作說明：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="3813d-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="3813d-165">逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="3813d-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="3813d-166">元件撰寫</span><span class="sxs-lookup"><span data-stu-id="3813d-166">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="3813d-167">疑難排解設計階段開發</span><span class="sxs-lookup"><span data-stu-id="3813d-167">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="3813d-168">使用元件進行程式設計</span><span class="sxs-lookup"><span data-stu-id="3813d-168">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
