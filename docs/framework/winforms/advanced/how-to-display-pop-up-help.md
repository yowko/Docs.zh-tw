---
title: 如何：顯示快顯說明
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: 47833e734c09e402ab1824b9c629b2ba39acfb9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43725003"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="91514-102">如何：顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="91514-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="91514-103">若要在 Windows Form 上顯示說明的方法之一是透過**幫助**按鈕位於標題列，可透過存取右側<xref:System.Windows.Forms.Form.HelpButton%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="91514-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="91514-104">這種顯示 [說明] 的方式非常適合與對話方塊一起使用。</span><span class="sxs-lookup"><span data-stu-id="91514-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="91514-105">以強制回應方式 (使用 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法) 顯示的對話方塊無法啟動外部 [說明] 系統，因為將焦點轉換至另一個視窗之前，必須先關閉強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91514-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="91514-106">此外，使用**幫助** 按鈕可讓您需要有沒有**最小化** 按鈕或**最大化**標題列中顯示的按鈕。</span><span class="sxs-lookup"><span data-stu-id="91514-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="91514-107">這是標準的對話方塊慣例，而表單則通常具有**最小化**並**最大化**按鈕。</span><span class="sxs-lookup"><span data-stu-id="91514-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="91514-108">請注意，您也可以使用 <xref:System.Windows.Forms.HelpProvider> 元件將控制項連結至 [說明] 系統中的檔案，即使您已實作快顯 [說明] 亦然。</span><span class="sxs-lookup"><span data-stu-id="91514-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="91514-109">如需詳細資訊，請參閱 < [Windows 應用程式中提供幫助](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)。</span><span class="sxs-lookup"><span data-stu-id="91514-109">For more information, see [Providing Help in a Windows Application](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91514-110">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="91514-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="91514-111">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="91514-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="91514-112">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="91514-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="91514-113">顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="91514-113">To display pop-up Help</span></span>  
  
1.  <span data-ttu-id="91514-114">拖曳[HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)元件從工具箱拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="91514-114">Drag a [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="91514-115">該元件會位於 Windows Form 設計工具底部的系統匣中。</span><span class="sxs-lookup"><span data-stu-id="91514-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="91514-116">在 [屬性] 視窗中，將 <xref:System.Windows.Forms.Form.HelpButton%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="91514-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="91514-117">表單的標題列右側會顯示一個有問號的按鈕。</span><span class="sxs-lookup"><span data-stu-id="91514-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3.  <span data-ttu-id="91514-118">為了顯示 <xref:System.Windows.Forms.Form.HelpButton%2A>，您必須將表單的 <xref:System.Windows.Forms.Form.MinimizeBox%2A> 和 <xref:System.Windows.Forms.Form.MaximizeBox%2A> 屬性設定為 `false`；將 <xref:System.Windows.Forms.Form.ControlBox%2A> 屬性設定為 `true`；並將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為下列其中一個值：<xref:System.Windows.Forms.FormBorderStyle.FixedSingle>、<xref:System.Windows.Forms.FormBorderStyle.Fixed3D>、<xref:System.Windows.Forms.FormBorderStyle.FixedDialog> 或 <xref:System.Windows.Forms.FormBorderStyle.Sizable>。</span><span class="sxs-lookup"><span data-stu-id="91514-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4.  <span data-ttu-id="91514-119">選取您要在表單上顯示 [說明] 的控制項，並在 [屬性] 視窗中設定 [說明] 字串。</span><span class="sxs-lookup"><span data-stu-id="91514-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="91514-120">這是會在類似於視窗中顯示的文字字串[工具提示](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="91514-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span></span>  
  
5.  <span data-ttu-id="91514-121">請按 **F5**。</span><span class="sxs-lookup"><span data-stu-id="91514-121">Press **F5**.</span></span>  
  
6.  <span data-ttu-id="91514-122">按下**協助**按鈕標題列上，然後按一下您要在其設定的說明字串的控制項。</span><span class="sxs-lookup"><span data-stu-id="91514-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91514-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91514-123">See Also</span></span>  
 [<span data-ttu-id="91514-124">使用工具提示來顯示控制項說明</span><span class="sxs-lookup"><span data-stu-id="91514-124">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="91514-125">整合 Windows Forms 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="91514-125">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="91514-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91514-126">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
