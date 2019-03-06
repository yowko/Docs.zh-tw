---
title: HOW TO：啟用混合式應用程式中的視覺化樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 9588a2e2d839af43ffe4397303c4a45cad5af2e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371914"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="62733-102">HOW TO：啟用混合式應用程式中的視覺化樣式</span><span class="sxs-lookup"><span data-stu-id="62733-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="62733-103">本主題說明如何啟用[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]視覺化樣式上[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項裝載於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62733-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="62733-104">如果您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法，則大部分您[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上執行您的應用程式時，控制項將會自動使用視覺化樣式[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62733-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="62733-105">如需詳細資訊，請參閱 <<c0> [ 呈現具有視覺化樣式的控制項](../../winforms/controls/rendering-controls-with-visual-styles.md)。</span><span class="sxs-lookup"><span data-stu-id="62733-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="62733-106">如本主題中所述工作的完整程式碼清單，請參閱 <<c0> [ 啟用混合式應用程式範例中的視覺化樣式](https://go.microsoft.com/fwlink/?LinkID=159986)。</span><span class="sxs-lookup"><span data-stu-id="62733-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="62733-107">啟用 Windows Forms 視覺化樣式</span><span class="sxs-lookup"><span data-stu-id="62733-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="62733-108">啟用 Windows Forms 視覺化樣式</span><span class="sxs-lookup"><span data-stu-id="62733-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="62733-109">建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式專案，名為`HostingWfWithVisualStyles`。</span><span class="sxs-lookup"><span data-stu-id="62733-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="62733-110">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="62733-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="62733-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="62733-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="62733-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="62733-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="62733-113">在 [工具箱] 中，按兩下<xref:System.Windows.Controls.Grid>圖示，以放置<xref:System.Windows.Controls.Grid>設計介面上的項目。</span><span class="sxs-lookup"><span data-stu-id="62733-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="62733-114">在 [屬性] 視窗中設定的值<xref:System.Windows.FrameworkElement.Height%2A>並<xref:System.Windows.FrameworkElement.Width%2A>屬性，以**自動**。</span><span class="sxs-lookup"><span data-stu-id="62733-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="62733-115">在 設計 檢視或 XAML 檢視中，選取  <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="62733-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="62733-116">在 屬性 視窗中，按一下**事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="62733-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="62733-117">按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="62733-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="62733-118">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="62733-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="62733-119">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="62733-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="62733-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項繪製具有視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="62733-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="62733-121">停用 Windows Forms 視覺化樣式</span><span class="sxs-lookup"><span data-stu-id="62733-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="62733-122">若要停用視覺化樣式，只要移除呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="62733-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="62733-123">停用 Windows Forms 視覺化樣式</span><span class="sxs-lookup"><span data-stu-id="62733-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="62733-124">在程式碼編輯器中，開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="62733-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="62733-125">標記為註解的呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="62733-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="62733-126">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="62733-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="62733-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項使用預設系統樣式所繪製。</span><span class="sxs-lookup"><span data-stu-id="62733-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62733-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62733-128">See also</span></span>
- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="62733-129">使用視覺化樣式呈現控制項</span><span class="sxs-lookup"><span data-stu-id="62733-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="62733-130">逐步解說：裝載在 WPF 中的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="62733-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
