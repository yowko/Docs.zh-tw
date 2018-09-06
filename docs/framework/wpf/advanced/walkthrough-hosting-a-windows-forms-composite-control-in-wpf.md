---
title: 逐步解說：在 WPF 中裝載 Windows Form 複合控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22bfcf63fa42e72b3b971b18b5e68aec1e57c649
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859406"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="eed65-102">逐步解說：在 WPF 中裝載 Windows Form 複合控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="eed65-103"> 提供用來建立應用程式的豐富環境。</span><span class="sxs-lookup"><span data-stu-id="eed65-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="eed65-104">不過，如果您已長期開發[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]程式碼，它可以更有效率地重複使用至少其中某些程式碼中您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式而不從頭重寫程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="eed65-105">最常見的案例是當您有現有的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="eed65-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="eed65-106">在某些情況下，您甚至可能無法存取這些控制項的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="eed65-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="eed65-107"> 提供簡單的程序這類控制項裝載於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="eed65-108">例如，您可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]適用於大部分的程式設計時裝載您特殊<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="eed65-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="eed65-109">本逐步解說將引導您透過應用程式裝載 Windows Forms 複合控制項，以執行中的資料輸入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="eed65-110">複合控制項會封裝在 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="eed65-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="eed65-111">這個一般程序可以延伸到更複雜的應用程式和控制項。</span><span class="sxs-lookup"><span data-stu-id="eed65-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="eed65-112">本逐步解說設計成幾乎完全相同的外觀和功能[逐步解說： 裝載 Windows Forms 中的 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="eed65-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="eed65-113">主要差異在於裝載案例相反。</span><span class="sxs-lookup"><span data-stu-id="eed65-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="eed65-114">本逐步解說分為兩節。</span><span class="sxs-lookup"><span data-stu-id="eed65-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="eed65-115">第一節簡要說明 Windows Forms 複合控制項的實作。</span><span class="sxs-lookup"><span data-stu-id="eed65-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="eed65-116">第二節詳細討論如何裝載複合控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，接收來自控制項，事件，以及存取某些控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="eed65-117">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="eed65-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="eed65-118">實作 Windows Forms 複合控制項。</span><span class="sxs-lookup"><span data-stu-id="eed65-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="eed65-119">實作 WPF 主應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="eed65-120">在此逐步解說中所述工作的完整程式碼清單，請參閱 <<c0> [ 裝載在 WPF 範例中的 Windows Forms 複合控制項](https://go.microsoft.com/fwlink/?LinkID=159999)。</span><span class="sxs-lookup"><span data-stu-id="eed65-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eed65-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="eed65-121">Prerequisites</span></span>  
 <span data-ttu-id="eed65-122">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="eed65-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="eed65-123">.</span><span class="sxs-lookup"><span data-stu-id="eed65-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="eed65-124">實作 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="eed65-125">此範例中使用 Windows Forms 複合控制項是簡單的資料輸入表單。</span><span class="sxs-lookup"><span data-stu-id="eed65-125">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="eed65-126">此表單採用使用者名稱和地址，然後使用自訂事件將該資訊傳回給主應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="eed65-127">下圖顯示轉譯的控制項。</span><span class="sxs-lookup"><span data-stu-id="eed65-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="eed65-128">![簡單的 Windows Form 控制項](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="eed65-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="eed65-129">Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="eed65-130">建立專案</span><span class="sxs-lookup"><span data-stu-id="eed65-130">Creating the Project</span></span>  
 <span data-ttu-id="eed65-131">啟動專案：</span><span class="sxs-lookup"><span data-stu-id="eed65-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="eed65-132">啟動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，然後開啟**新的專案** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="eed65-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="eed65-133">在 Window 分類中，選取**Windows Form 控制項程式庫**範本。</span><span class="sxs-lookup"><span data-stu-id="eed65-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="eed65-134">將新專案命名為 `MyControls`。</span><span class="sxs-lookup"><span data-stu-id="eed65-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="eed65-135">針對位置，指定方便命名的最上層資料夾，例如`WpfHostingWindowsFormsControl`。</span><span class="sxs-lookup"><span data-stu-id="eed65-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="eed65-136">稍後，您會將主應用程式放在此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="eed65-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="eed65-137">按一下 [確定] 建立專案。</span><span class="sxs-lookup"><span data-stu-id="eed65-137">Click **OK** to create the project.</span></span> <span data-ttu-id="eed65-138">預設專案會包含名為的單一控制項`UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="eed65-139">在 [方案總管] 中，重新命名`UserControl1`至`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="eed65-140">您的專案應該有下列系統 DLL 的參考。</span><span class="sxs-lookup"><span data-stu-id="eed65-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="eed65-141">如果預設未包括所有這些 DLL，則請將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="eed65-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="eed65-142">系統</span><span class="sxs-lookup"><span data-stu-id="eed65-142">System</span></span>  
  
-   <span data-ttu-id="eed65-143">System.Data</span><span class="sxs-lookup"><span data-stu-id="eed65-143">System.Data</span></span>  
  
-   <span data-ttu-id="eed65-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="eed65-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="eed65-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="eed65-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="eed65-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="eed65-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="eed65-147">將控制項加入至表單</span><span class="sxs-lookup"><span data-stu-id="eed65-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="eed65-148">將控制項新增至表單：</span><span class="sxs-lookup"><span data-stu-id="eed65-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="eed65-149">開啟`MyControl1`設計工具中。</span><span class="sxs-lookup"><span data-stu-id="eed65-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="eed65-150">新增五<xref:System.Windows.Forms.Label>控制項和其對應<xref:System.Windows.Forms.TextBox>控制項、 大小和排列以其在上圖中，在表單上。</span><span class="sxs-lookup"><span data-stu-id="eed65-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="eed65-151">在範例中，<xref:System.Windows.Forms.TextBox>控制項命名為：</span><span class="sxs-lookup"><span data-stu-id="eed65-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="eed65-152">新增兩個<xref:System.Windows.Forms.Button>標示為控制項 **[確定]** 並**取消**。</span><span class="sxs-lookup"><span data-stu-id="eed65-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="eed65-153">在此範例中，為餂鈕晻`btnOK`和`btnCancel`分別。</span><span class="sxs-lookup"><span data-stu-id="eed65-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="eed65-154">實作支援程式碼</span><span class="sxs-lookup"><span data-stu-id="eed65-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="eed65-155">在程式碼檢視中，開啟表單。</span><span class="sxs-lookup"><span data-stu-id="eed65-155">Open the form in code view.</span></span> <span data-ttu-id="eed65-156">控制項會返回至其主應用程式所收集的資料，藉由引發自訂`OnButtonClick`事件。</span><span class="sxs-lookup"><span data-stu-id="eed65-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="eed65-157">此資料包含在事件引數物件中。</span><span class="sxs-lookup"><span data-stu-id="eed65-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="eed65-158">下列程式碼示範事件和委派宣告。</span><span class="sxs-lookup"><span data-stu-id="eed65-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="eed65-159">將下列程式碼加入 `MyControl1` 類別。</span><span class="sxs-lookup"><span data-stu-id="eed65-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="eed65-160">`MyControlEventArgs`類別包含要傳回給主應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="eed65-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="eed65-161">將下列類別新增至表單。</span><span class="sxs-lookup"><span data-stu-id="eed65-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="eed65-162">當使用者按一下**確定**或**取消** 按鈕<xref:System.Windows.Forms.Control.Click>事件處理常式建立`MyControlEventArgs`物件，其中包含資料，並引發`OnButtonClick`事件。</span><span class="sxs-lookup"><span data-stu-id="eed65-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="eed65-163">兩個處理常式之間唯一的差別在於事件引數的`IsOK`屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="eed65-164">此屬性可讓主應用程式判斷所按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="eed65-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="eed65-165">設為`true`for **確定**  按鈕，和`false`如**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eed65-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="eed65-166">下列程式碼示範兩個按鈕處理常式。</span><span class="sxs-lookup"><span data-stu-id="eed65-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="eed65-167">將下列程式碼加入 `MyControl1` 類別。</span><span class="sxs-lookup"><span data-stu-id="eed65-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="eed65-168">提供組件的強式名稱以及建置組件</span><span class="sxs-lookup"><span data-stu-id="eed65-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="eed65-169">所要參考這個組件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，它必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="eed65-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="eed65-170">若要建立強式名稱，請使用 Sn.exe 建立金鑰檔並將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="eed65-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="eed65-171">開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="eed65-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="eed65-172">若要這樣做，請按一下**開始** 功能表，然後選取**所有程式 /microsoft Visual Studio 2010/Visual Studio 工具/Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="eed65-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="eed65-173">這會使用自訂的環境變數來啟動主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="eed65-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="eed65-174">在命令提示字元中，使用`cd`命令來移至您的專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="eed65-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="eed65-175">執行下列命令，以產生名為 MyControls.snk 的金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="eed65-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="eed65-176">若要在專案中包含的金鑰檔，以滑鼠右鍵按一下方案總管] 中的專案名稱，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="eed65-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="eed65-177">在 專案設計工具中，按一下**Signing**索引標籤上，選取**簽署組件**核取方塊，然後瀏覽至您的金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="eed65-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="eed65-178">建置方案。</span><span class="sxs-lookup"><span data-stu-id="eed65-178">Build the solution.</span></span> <span data-ttu-id="eed65-179">組置將會產生名為 MyControls.dll 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="eed65-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="eed65-180">實作 WPF 主應用程式</span><span class="sxs-lookup"><span data-stu-id="eed65-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="eed65-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載應用程式會使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項來裝載`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="eed65-182">應用程式會處理`OnButtonClick`事件，以接收來自控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="eed65-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="eed65-183">它也會有的選項按鈕，可讓您變更某些控制項的屬性，從集合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="eed65-184">下圖顯示已完成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="eed65-185">![內嵌於 WPF 頁面中的控制項](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="eed65-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="eed65-186">完整應用程式，顯示內嵌於 WPF 應用程式中的控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="eed65-187">建立專案</span><span class="sxs-lookup"><span data-stu-id="eed65-187">Creating the Project</span></span>  
 <span data-ttu-id="eed65-188">啟動專案：</span><span class="sxs-lookup"><span data-stu-id="eed65-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="eed65-189">開啟[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取**新的專案**。</span><span class="sxs-lookup"><span data-stu-id="eed65-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="eed65-190">在 Window 分類中，選取**WPF 應用程式**範本。</span><span class="sxs-lookup"><span data-stu-id="eed65-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="eed65-191">將新專案命名為 `WpfHost`。</span><span class="sxs-lookup"><span data-stu-id="eed65-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="eed65-192">針對位置，指定包含 MyControls 專案的相同最上層資料夾。</span><span class="sxs-lookup"><span data-stu-id="eed65-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="eed65-193">按一下 [確定] 建立專案。</span><span class="sxs-lookup"><span data-stu-id="eed65-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="eed65-194">您也需要將參考加入至包含的 DLL`MyControl1`和其他組件。</span><span class="sxs-lookup"><span data-stu-id="eed65-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="eed65-195">以滑鼠右鍵按一下方案總管 中的專案名稱，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="eed65-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="eed65-196">按一下 **瀏覽**索引標籤，然後瀏覽至包含 MyControls.dll 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="eed65-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="eed65-197">在此逐步解說中，這個資料夾是 MyControls\bin\Debug。</span><span class="sxs-lookup"><span data-stu-id="eed65-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="eed65-198">選取 MyControls.dll，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="eed65-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="eed65-199">加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="eed65-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="eed65-200">實作基本版面配置</span><span class="sxs-lookup"><span data-stu-id="eed65-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="eed65-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主應用程式的應用程式在 MainWindow.xaml 中實作。</span><span class="sxs-lookup"><span data-stu-id="eed65-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="eed65-202">此檔案包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義版面配置，並裝載在 Windows Form 控制項的標記。</span><span class="sxs-lookup"><span data-stu-id="eed65-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="eed65-203">應用程式分為三個區域：</span><span class="sxs-lookup"><span data-stu-id="eed65-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="eed65-204">**控制項屬性**面板，其中包含一組選項按鈕可供您修改託管控制項的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="eed65-205">**Data from Control**面板中，其中包含數個<xref:System.Windows.Controls.TextBlock>傳回從裝載控制項的顯示資料的項目。</span><span class="sxs-lookup"><span data-stu-id="eed65-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="eed65-206">託管控制項本身。</span><span class="sxs-lookup"><span data-stu-id="eed65-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="eed65-207">下列 XAML 會顯示基本版面配置。</span><span class="sxs-lookup"><span data-stu-id="eed65-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="eed65-208">需要的標記至主機`MyControl1`會略過此範例中，但將在稍後討論。</span><span class="sxs-lookup"><span data-stu-id="eed65-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="eed65-209">將 MainWindow.xaml 中的 XAML 取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eed65-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="eed65-210">如果您使用 Visual Basic，將類別變更為`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="eed65-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="eed65-211">第一個<xref:System.Windows.Controls.StackPanel>項目包含幾組<xref:System.Windows.Controls.RadioButton>控制項，可讓您修改託管控制項的各種預設屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="eed65-212">接著就<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，哪些主機`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="eed65-213">最終<xref:System.Windows.Controls.StackPanel>項目包含數個<xref:System.Windows.Controls.TextBlock>顯示託管控制項傳回之資料的項目。</span><span class="sxs-lookup"><span data-stu-id="eed65-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="eed65-214">項目的排序並<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性設定託管的控制項嵌入視窗而沒有間距或失真。</span><span class="sxs-lookup"><span data-stu-id="eed65-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="eed65-215">裝載控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-215">Hosting the Control</span></span>  
 <span data-ttu-id="eed65-216">前一個 XAML 的下列編輯過的版本著重於所需的項目來裝載`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="eed65-217">`xmlns`命名空間對應屬性會建立參考`MyControls`包含託管的控制項的命名空間。</span><span class="sxs-lookup"><span data-stu-id="eed65-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="eed65-218">此對應可讓您代表`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]做為`<mcl:MyControl1>`。</span><span class="sxs-lookup"><span data-stu-id="eed65-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="eed65-219">XAML 中有兩個項目可處理裝載︰</span><span class="sxs-lookup"><span data-stu-id="eed65-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="eed65-220">`WindowsFormsHost` 代表<xref:System.Windows.Forms.Integration.WindowsFormsHost>可讓您裝載 Windows Form 控制項中的項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="eed65-221">`mcl:MyControl1`表示`MyControl1`，新增至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子集合。</span><span class="sxs-lookup"><span data-stu-id="eed65-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="eed65-222">如此一來，這個 Windows Form 控制項呈現為一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗中，而且您可以與應用程式的來源控制項進行通訊。</span><span class="sxs-lookup"><span data-stu-id="eed65-222">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="eed65-223">實作程式碼後置檔案</span><span class="sxs-lookup"><span data-stu-id="eed65-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="eed65-224">程式碼後置檔案 MainWindow.xaml.vb 或 MainWindow.xaml.cs 包含實作的功能的程序性程式碼[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上一節所述。</span><span class="sxs-lookup"><span data-stu-id="eed65-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="eed65-225">主要工作如下︰</span><span class="sxs-lookup"><span data-stu-id="eed65-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="eed65-226">附加事件處理常式`MyControl1`的`OnButtonClick`事件。</span><span class="sxs-lookup"><span data-stu-id="eed65-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="eed65-227">修改的各種屬性`MyControl1`根據組選項按鈕的設定方式。</span><span class="sxs-lookup"><span data-stu-id="eed65-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="eed65-228">顯示控制項所收集到的資料。</span><span class="sxs-lookup"><span data-stu-id="eed65-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="eed65-229">初始化應用程式</span><span class="sxs-lookup"><span data-stu-id="eed65-229">Initializing the Application</span></span>  
 <span data-ttu-id="eed65-230">初始化程式碼包含在視窗的事件處理常式<xref:System.Windows.FrameworkElement.Loaded>事件，並將事件處理常式附加至控制項的`OnButtonClick`事件。</span><span class="sxs-lookup"><span data-stu-id="eed65-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="eed65-231">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，加入下列程式碼`MainWindow`類別。</span><span class="sxs-lookup"><span data-stu-id="eed65-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="eed65-232">因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]討論先前加入`MyControl1`要<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子項目集合，您可以轉換<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>若要取得參考`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="eed65-233">您接著可以使用該參考來附加事件處理常式`OnButtonClick`。</span><span class="sxs-lookup"><span data-stu-id="eed65-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="eed65-234">除了提供控制項本身的參考<xref:System.Windows.Forms.Integration.WindowsFormsHost>顯示幾個控制項的屬性，您可以從應用程式來處理。</span><span class="sxs-lookup"><span data-stu-id="eed65-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="eed65-235">初始化程式碼會將這些值指派給私用全域變數，以供稍後在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="eed65-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="eed65-236">好讓您可以輕鬆地存取中的型別`MyControls`DLL，新增下列`Imports`或`using`至檔案頂端的陳述式。</span><span class="sxs-lookup"><span data-stu-id="eed65-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="eed65-237">處理 OnButtonClick 事件</span><span class="sxs-lookup"><span data-stu-id="eed65-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="eed65-238">`MyControl1` 引發`OnButtonClick`事件，當使用者按一下其中一個控制項的按鈕。</span><span class="sxs-lookup"><span data-stu-id="eed65-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="eed65-239">將下列程式碼加入 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="eed65-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="eed65-240">在文字方塊中的資料會封裝到`MyControlEventArgs`物件。</span><span class="sxs-lookup"><span data-stu-id="eed65-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="eed65-241">如果使用者按一下**確定**  按鈕，事件處理常式會擷取資料並將它顯示在下面的面板`MyControl1`。</span><span class="sxs-lookup"><span data-stu-id="eed65-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="eed65-242">修改控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="eed65-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="eed65-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會公開數個裝載的控制項預設屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="eed65-244">因此，您可以變更控制項的外觀，更密切符合應用程式的樣式。</span><span class="sxs-lookup"><span data-stu-id="eed65-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="eed65-245">左面板中的多組選項按鈕可讓使用者修改數個色彩和字型屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="eed65-246">每一組按鈕具有的處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，以偵測到使用者的選項按鈕選取項目，並變更控制項上的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="eed65-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="eed65-247">將下列程式碼加入 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="eed65-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="eed65-248">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed65-248">Build and run the application.</span></span> <span data-ttu-id="eed65-249">在 Windows Forms 複合控制項中新增一些文字，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="eed65-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="eed65-250">文字會顯示在標籤中。</span><span class="sxs-lookup"><span data-stu-id="eed65-250">The text appears in the labels.</span></span> <span data-ttu-id="eed65-251">按一下不同的選項按鈕，以查看在控制項上的效果。</span><span class="sxs-lookup"><span data-stu-id="eed65-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed65-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed65-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="eed65-253">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="eed65-253">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="eed65-254">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="eed65-255">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="eed65-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
