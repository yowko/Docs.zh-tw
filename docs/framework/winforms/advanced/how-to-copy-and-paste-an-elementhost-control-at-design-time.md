---
title: 如何：在設計階段複製和貼上 ElementHost 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: a61a8538fb9b4245e3f3705c5d5cbb1b45ed0b72
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266158"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="90121-102">如何：在設計階段複製和貼上 ElementHost 控制項</span><span class="sxs-lookup"><span data-stu-id="90121-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="90121-103">此程序會示範如何複製 Windows Form 上的 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="90121-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90121-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="90121-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="90121-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="90121-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="90121-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="90121-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="90121-107">複製並貼上 ElementHost 控制項在設計階段</span><span class="sxs-lookup"><span data-stu-id="90121-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="90121-108">將新的 WPF<xref:System.Windows.Controls.UserControl>至您的 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="90121-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="90121-109">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="90121-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="90121-110">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="90121-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="90121-111">在**屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>的屬性`UserControl1`至`200`。</span><span class="sxs-lookup"><span data-stu-id="90121-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="90121-112">將 <xref:System.Windows.Controls.Control.Background%2A> 屬性值設定為 `Blue`。</span><span class="sxs-lookup"><span data-stu-id="90121-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="90121-113">建置專案。</span><span class="sxs-lookup"><span data-stu-id="90121-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="90121-114">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="90121-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="90121-115">從**工具箱**，將拖曳的執行個體`UserControl1`拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="90121-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="90121-116">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="90121-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="90121-117">在選取 `elementHost1` 時，按 CTRL+C 將其複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="90121-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="90121-118">按下 CTRL + V 鍵貼上複製的控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="90121-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="90121-119">新<xref:System.Windows.Forms.Integration.ElementHost>控制項，名為`elementHost2`建立表單上。</span><span class="sxs-lookup"><span data-stu-id="90121-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90121-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90121-120">See Also</span></span>  

- <xref:System.Windows.Forms.Integration.ElementHost>  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
- [<span data-ttu-id="90121-121">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="90121-121">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
- [<span data-ttu-id="90121-122">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="90121-122">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
- [<span data-ttu-id="90121-123">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="90121-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)