---
title: 逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991876"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="9ae71-102">逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="9ae71-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="9ae71-103">提供用來建立應用程式的豐富環境。</span><span class="sxs-lookup"><span data-stu-id="9ae71-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="9ae71-104">不過，當您在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]程式碼中有大量的投資時，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的應用程式中重複使用至少其中一些程式碼，而不是從頭重新撰寫，可能會更有效率。</span><span class="sxs-lookup"><span data-stu-id="9ae71-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="9ae71-105">最常見的情況是當您有現有的 Windows Forms 控制項時。</span><span class="sxs-lookup"><span data-stu-id="9ae71-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="9ae71-106">在某些情況下，您甚至可能無法存取這些控制項的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ae71-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="9ae71-107">提供在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中裝載這類控制項的簡單程式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9ae71-108">例如，您可以在裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特定<xref:System.Windows.Forms.DataGridView>控制項時，在大部分的程式設計中使用。</span><span class="sxs-lookup"><span data-stu-id="9ae71-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="9ae71-109">本逐步解說會引導您完成裝載 Windows Forms 複合控制項的應用程式，以在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中執行資料輸入。</span><span class="sxs-lookup"><span data-stu-id="9ae71-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9ae71-110">複合控制項會封裝在 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="9ae71-111">這個一般程序可以延伸到更複雜的應用程式和控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="9ae71-112">本逐步解說的設計, 與[逐步解說的外觀和功能大致相同:在 Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)中裝載 WPF 複合控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="9ae71-113">主要差異在於裝載案例相反。</span><span class="sxs-lookup"><span data-stu-id="9ae71-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="9ae71-114">本逐步解說分為兩節。</span><span class="sxs-lookup"><span data-stu-id="9ae71-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="9ae71-115">第一節簡要描述 Windows Forms 複合控制項的執行。</span><span class="sxs-lookup"><span data-stu-id="9ae71-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="9ae71-116">第二節詳細討論如何在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中裝載複合控制項、接收來自控制項的事件，以及存取控制項的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="9ae71-117">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="9ae71-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="9ae71-118">實作 Windows Forms 複合控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="9ae71-119">實作 WPF 主應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="9ae71-120">如需本逐步解說中所述工作的完整程式代碼清單，請參閱[在 WPF 中裝載 Windows Forms 複合控制項範例](https://go.microsoft.com/fwlink/?LinkID=159999)。</span><span class="sxs-lookup"><span data-stu-id="9ae71-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9ae71-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="9ae71-121">Prerequisites</span></span>  

<span data-ttu-id="9ae71-122">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="9ae71-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="9ae71-123">實作 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="9ae71-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="9ae71-124">此範例中使用的 Windows Forms 複合控制項是簡單的資料輸入表單。</span><span class="sxs-lookup"><span data-stu-id="9ae71-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="9ae71-125">此表單採用使用者名稱和地址，然後使用自訂事件將該資訊傳回給主應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="9ae71-126">下圖顯示轉譯的控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="9ae71-127">下圖顯示 Windows Forms 複合控制項：</span><span class="sxs-lookup"><span data-stu-id="9ae71-127">The following image shows a Windows Forms composite control:</span></span>  

 ![顯示簡單 Windows Forms 控制項的螢幕擷取畫面。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="9ae71-129">建立專案</span><span class="sxs-lookup"><span data-stu-id="9ae71-129">Creating the Project</span></span>  
 <span data-ttu-id="9ae71-130">啟動專案：</span><span class="sxs-lookup"><span data-stu-id="9ae71-130">To start the project:</span></span>  
  
1. <span data-ttu-id="9ae71-131">啟動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], 然後開啟 [**新增專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ae71-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="9ae71-132">在 [視窗] 分類中，選取 [ **Windows Forms 控制項程式庫**] 範本。</span><span class="sxs-lookup"><span data-stu-id="9ae71-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="9ae71-133">將新專案命名為 `MyControls`。</span><span class="sxs-lookup"><span data-stu-id="9ae71-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="9ae71-134">在 [位置] 中, 指定方便命名的最上層資料夾, 例如`WpfHostingWindowsFormsControl`。</span><span class="sxs-lookup"><span data-stu-id="9ae71-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="9ae71-135">稍後，您會將主應用程式放在此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="9ae71-136">按一下 \[確定\] 來建立專案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-136">Click **OK** to create the project.</span></span> <span data-ttu-id="9ae71-137">預設專案包含名為`UserControl1`的單一控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="9ae71-138">在方案總管中, `UserControl1`將`MyControl1`重新命名為。</span><span class="sxs-lookup"><span data-stu-id="9ae71-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="9ae71-139">您的專案應該有下列系統 DLL 的參考。</span><span class="sxs-lookup"><span data-stu-id="9ae71-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="9ae71-140">如果預設未包括所有這些 DLL，則請將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="9ae71-141">系統</span><span class="sxs-lookup"><span data-stu-id="9ae71-141">System</span></span>  
  
- <span data-ttu-id="9ae71-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="9ae71-142">System.Data</span></span>  
  
- <span data-ttu-id="9ae71-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="9ae71-143">System.Drawing</span></span>  
  
- <span data-ttu-id="9ae71-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="9ae71-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="9ae71-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="9ae71-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="9ae71-146">將控制項加入至表單</span><span class="sxs-lookup"><span data-stu-id="9ae71-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="9ae71-147">將控制項新增至表單：</span><span class="sxs-lookup"><span data-stu-id="9ae71-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="9ae71-148">在`MyControl1`設計工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="9ae71-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="9ae71-149">在窗<xref:System.Windows.Forms.Label>體上新增五<xref:System.Windows.Forms.TextBox>個控制項及其對應的控制項、調整大小和相片順序（如上圖所示）。</span><span class="sxs-lookup"><span data-stu-id="9ae71-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="9ae71-150">在此範例中， <xref:System.Windows.Forms.TextBox>控制項的名稱為：</span><span class="sxs-lookup"><span data-stu-id="9ae71-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="9ae71-151">新增兩<xref:System.Windows.Forms.Button>個標示為 **[確定] 和 [** **取消**] 的控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="9ae71-152">在此範例中，按鈕名稱分別`btnOK`為`btnCancel`和。</span><span class="sxs-lookup"><span data-stu-id="9ae71-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="9ae71-153">實作支援程式碼</span><span class="sxs-lookup"><span data-stu-id="9ae71-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="9ae71-154">在程式碼檢視中，開啟表單。</span><span class="sxs-lookup"><span data-stu-id="9ae71-154">Open the form in code view.</span></span> <span data-ttu-id="9ae71-155">控制項會引發自訂`OnButtonClick`事件，以將收集的資料傳回給其主機。</span><span class="sxs-lookup"><span data-stu-id="9ae71-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="9ae71-156">此資料包含在事件引數物件中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="9ae71-157">下列程式碼示範事件和委派宣告。</span><span class="sxs-lookup"><span data-stu-id="9ae71-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="9ae71-158">將下列程式碼加入 `MyControl1` 類別。</span><span class="sxs-lookup"><span data-stu-id="9ae71-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="9ae71-159">`MyControlEventArgs`類別包含要傳回給主機的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ae71-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="9ae71-160">將下列類別新增至表單。</span><span class="sxs-lookup"><span data-stu-id="9ae71-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="9ae71-161">當使用者按一下 [**確定]** 或 **[取消** <xref:System.Windows.Forms.Control.Click> ] 按鈕時，事件處理常式會建立`MyControlEventArgs`包含資料的物件， `OnButtonClick`並引發事件。</span><span class="sxs-lookup"><span data-stu-id="9ae71-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="9ae71-162">這兩個處理常式的唯一差異在於事件引數`IsOK`的屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="9ae71-163">此屬性可讓主應用程式判斷所按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9ae71-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="9ae71-164">它會針對 [ `true` **確定]** 按鈕和`false` [**取消**] 按鈕設定為。</span><span class="sxs-lookup"><span data-stu-id="9ae71-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="9ae71-165">下列程式碼示範兩個按鈕處理常式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="9ae71-166">將下列程式碼加入 `MyControl1` 類別。</span><span class="sxs-lookup"><span data-stu-id="9ae71-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="9ae71-167">提供組件的強式名稱以及建置組件</span><span class="sxs-lookup"><span data-stu-id="9ae71-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="9ae71-168">若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式參考此元件，它必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae71-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="9ae71-169">若要建立強式名稱，請使用 Sn.exe 建立金鑰檔，並將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="9ae71-170">開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9ae71-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="9ae71-171">若要這麼做，請按一下 [**開始**] 功能表，然後選取 [**所有程式]/[Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio 命令提示**字元]。</span><span class="sxs-lookup"><span data-stu-id="9ae71-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="9ae71-172">這會使用自訂的環境變數來啟動主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="9ae71-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="9ae71-173">在命令提示字元中，使用`cd`命令來移至您的專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ae71-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="9ae71-174">執行下列命令，以產生名為 MyControls.snk 的金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="9ae71-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="9ae71-175">若要在專案中包含金鑰檔，請在方案總管中的專案名稱上按一下滑鼠右鍵，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="9ae71-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="9ae71-176">在 [專案設計工具] 中，按一下 [**簽署**] 索引標籤，選取 [**簽署元件**] 核取方塊，然後流覽至您的金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="9ae71-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="9ae71-177">建置方案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-177">Build the solution.</span></span> <span data-ttu-id="9ae71-178">組置將會產生名為 MyControls.dll 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="9ae71-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="9ae71-179">實作 WPF 主應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae71-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="9ae71-180">主應用程式會<xref:System.Windows.Forms.Integration.WindowsFormsHost>使用控制項來裝載`MyControl1`。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ae71-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="9ae71-181">應用程式會處理`OnButtonClick`事件，以接收來自控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="9ae71-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="9ae71-182">它也有一組選項按鈕，可讓您從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式變更部分控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9ae71-183">下圖顯示已完成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="9ae71-184">下圖顯示完整的應用程式，包括內嵌在 WPF 應用程式中的控制項：</span><span class="sxs-lookup"><span data-stu-id="9ae71-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![顯示內嵌于 WPF 頁面中之控制項的螢幕擷取畫面。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="9ae71-186">建立專案</span><span class="sxs-lookup"><span data-stu-id="9ae71-186">Creating the Project</span></span>
 <span data-ttu-id="9ae71-187">啟動專案：</span><span class="sxs-lookup"><span data-stu-id="9ae71-187">To start the project:</span></span>

1. <span data-ttu-id="9ae71-188">開啟[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="9ae71-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="9ae71-189">在 [視窗] 分類中，選取 [ **WPF 應用程式**] 範本。</span><span class="sxs-lookup"><span data-stu-id="9ae71-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="9ae71-190">將新專案命名為 `WpfHost`。</span><span class="sxs-lookup"><span data-stu-id="9ae71-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="9ae71-191">針對位置，指定包含 MyControls 專案的相同最上層資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ae71-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="9ae71-192">按一下 \[確定\] 來建立專案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="9ae71-193">您也需要加入包含`MyControl1`和其他元件之 DLL 的參考。</span><span class="sxs-lookup"><span data-stu-id="9ae71-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="9ae71-194">以滑鼠右鍵按一下方案總管中的專案名稱，然後選取 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="9ae71-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="9ae71-195">按一下 [**流覽**] 索引標籤, 然後流覽至包含 mycontrols.dll 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ae71-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="9ae71-196">在此逐步解說中，這個資料夾是 MyControls\bin\Debug。</span><span class="sxs-lookup"><span data-stu-id="9ae71-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="9ae71-197">選取 [Mycontrols.dll], 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ae71-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="9ae71-198">加入 WindowsFormsIntegration 元件的參考，其名稱為 WindowsFormsIntegration。</span><span class="sxs-lookup"><span data-stu-id="9ae71-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="9ae71-199">實作基本版面配置</span><span class="sxs-lookup"><span data-stu-id="9ae71-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="9ae71-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主應用程式的會在 mainwindow.xaml 中執行。</span><span class="sxs-lookup"><span data-stu-id="9ae71-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="9ae71-201">這個檔案包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義配置的標記，以及主控 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae71-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="9ae71-202">應用程式分為三個區域：</span><span class="sxs-lookup"><span data-stu-id="9ae71-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="9ae71-203">[**控制項屬性**] 面板，其中包含選項按鈕的集合，您可以用來修改裝載控制項的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="9ae71-204">[**控制台**] 中的資料，其中包含<xref:System.Windows.Controls.TextBlock>數個專案，這些專案會顯示從裝載控制項傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="9ae71-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="9ae71-205">託管控制項本身。</span><span class="sxs-lookup"><span data-stu-id="9ae71-205">The hosted control itself.</span></span>

 <span data-ttu-id="9ae71-206">下列 XAML 會顯示基本版面配置。</span><span class="sxs-lookup"><span data-stu-id="9ae71-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="9ae71-207">這個範例會省略裝載`MyControl1`所需的標記，但稍後會討論。</span><span class="sxs-lookup"><span data-stu-id="9ae71-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="9ae71-208">將 MainWindow.xaml 中的 XAML 取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ae71-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="9ae71-209">如果您使用 Visual Basic，請將類別變更為`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="9ae71-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="9ae71-210">第一個<xref:System.Windows.Controls.StackPanel>元素包含數個<xref:System.Windows.Controls.RadioButton>控制項集合，可讓您修改裝載控制項的各種預設屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="9ae71-211">後面接著<xref:System.Windows.Forms.Integration.WindowsFormsHost>裝載`MyControl1`的元素。</span><span class="sxs-lookup"><span data-stu-id="9ae71-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="9ae71-212">最後一個<xref:System.Windows.Controls.StackPanel>元素包含數<xref:System.Windows.Controls.TextBlock>個專案，這些專案會顯示裝載控制項所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="9ae71-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="9ae71-213">專案的順序和<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性設定會將裝載的控制項內嵌到視窗中，而且不會有間距或失真。</span><span class="sxs-lookup"><span data-stu-id="9ae71-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="9ae71-214">裝載控制項</span><span class="sxs-lookup"><span data-stu-id="9ae71-214">Hosting the Control</span></span>
 <span data-ttu-id="9ae71-215">舊版 XAML 的下列已編輯版本著重于裝載`MyControl1`所需的專案。</span><span class="sxs-lookup"><span data-stu-id="9ae71-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="9ae71-216">命名空間對應屬性會建立包含主控控制項`MyControls`之命名空間的參考。 `xmlns`</span><span class="sxs-lookup"><span data-stu-id="9ae71-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="9ae71-217">這個對應可讓您將`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的`<mcl:MyControl1>`表示為。</span><span class="sxs-lookup"><span data-stu-id="9ae71-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="9ae71-218">XAML 中有兩個項目可處理裝載︰</span><span class="sxs-lookup"><span data-stu-id="9ae71-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="9ae71-219">`WindowsFormsHost`表示可讓您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在應用程式中裝載 Windows Forms 控制項的元素。<xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="9ae71-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="9ae71-220">`mcl:MyControl1`，其代表`MyControl1`會加入<xref:System.Windows.Forms.Integration.WindowsFormsHost>至專案的子集合。</span><span class="sxs-lookup"><span data-stu-id="9ae71-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="9ae71-221">如此一來，這個 Windows Forms 控制項會呈現為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗的一部分，而且您可以從應用程式與控制項進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9ae71-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="9ae71-222">實作程式碼後置檔案</span><span class="sxs-lookup"><span data-stu-id="9ae71-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="9ae71-223">程式碼後置檔案 mainwindow.xaml 或 MainWindow.xaml.cs 包含程式碼，可執行上一節中所討論的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="9ae71-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="9ae71-224">主要工作如下︰</span><span class="sxs-lookup"><span data-stu-id="9ae71-224">The primary tasks are:</span></span>

- <span data-ttu-id="9ae71-225">將事件處理常式附加`MyControl1`到`OnButtonClick`的事件。</span><span class="sxs-lookup"><span data-stu-id="9ae71-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="9ae71-226">根據設定選項按鈕`MyControl1`集合的方式，修改的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="9ae71-227">顯示控制項所收集到的資料。</span><span class="sxs-lookup"><span data-stu-id="9ae71-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="9ae71-228">初始化應用程式</span><span class="sxs-lookup"><span data-stu-id="9ae71-228">Initializing the Application</span></span>
 <span data-ttu-id="9ae71-229">初始化程式碼包含在視窗<xref:System.Windows.FrameworkElement.Loaded>事件的事件處理常式中，並將事件處理常式附加至控制項的`OnButtonClick`事件。</span><span class="sxs-lookup"><span data-stu-id="9ae71-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="9ae71-230">在 mainwindow.xaml 或 MainWindow.xaml.cs 中，將下列程式碼新增至`MainWindow`類別。</span><span class="sxs-lookup"><span data-stu-id="9ae71-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="9ae71-231">由於先前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]所討論的`MyControl1`專案是<xref:System.Windows.Forms.Integration.WindowsFormsHost>加入至專案的<xref:System.Windows.Forms.Integration.WindowsFormsHost>子專案集合，因此您可以轉換<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>專案的來取得的`MyControl1`參考。</span><span class="sxs-lookup"><span data-stu-id="9ae71-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="9ae71-232">然後，您可以使用該參考，將事件處理常式`OnButtonClick`附加至。</span><span class="sxs-lookup"><span data-stu-id="9ae71-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="9ae71-233">除了提供控制項本身的參考之外， <xref:System.Windows.Forms.Integration.WindowsFormsHost>還會公開一些控制項的屬性，讓您可以從應用程式操作。</span><span class="sxs-lookup"><span data-stu-id="9ae71-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="9ae71-234">初始化程式碼會將這些值指派給私用全域變數，以供稍後在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="9ae71-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="9ae71-235">因此，您可以輕鬆地存取`MyControls` DLL 中的類型，請將下列`Imports`或`using`語句加入檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="9ae71-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="9ae71-236">處理 OnButtonClick 事件</span><span class="sxs-lookup"><span data-stu-id="9ae71-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="9ae71-237">`MyControl1`當使用者`OnButtonClick`按一下控制項的其中一個按鈕時，會引發事件。</span><span class="sxs-lookup"><span data-stu-id="9ae71-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="9ae71-238">將下列程式碼加入 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="9ae71-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="9ae71-239">文字方塊中的資料會封裝到`MyControlEventArgs`物件中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="9ae71-240">如果使用者按一下 [**確定]** 按鈕，事件處理常式就會解壓縮資料，並將其顯示在`MyControl1`下方的面板中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="9ae71-241">修改控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="9ae71-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="9ae71-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會公開數個託管控制項的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="9ae71-243">因此，您可以變更控制項的外觀，更密切符合應用程式的樣式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="9ae71-244">左面板中的多組選項按鈕可讓使用者修改數個色彩和字型屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="9ae71-245">每組按鈕都有<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的處理常式，它會偵測使用者的選項按鈕選項，並變更控制項的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae71-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="9ae71-246">將下列程式碼加入 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="9ae71-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="9ae71-247">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae71-247">Build and run the application.</span></span> <span data-ttu-id="9ae71-248">在 Windows Forms 複合控制項中新增一些文字，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ae71-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="9ae71-249">文字會顯示在標籤中。</span><span class="sxs-lookup"><span data-stu-id="9ae71-249">The text appears in the labels.</span></span> <span data-ttu-id="9ae71-250">按一下不同的選項按鈕，以查看在控制項上的效果。</span><span class="sxs-lookup"><span data-stu-id="9ae71-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae71-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae71-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="9ae71-252">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="9ae71-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="9ae71-253">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="9ae71-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="9ae71-254">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="9ae71-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
