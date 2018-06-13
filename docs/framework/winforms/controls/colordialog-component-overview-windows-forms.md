---
title: ColorDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526034"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="755c4-102">ColorDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="755c4-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="755c4-103">Windows Form<xref:System.Windows.Forms.ColorDialog>元件是預先設定的對話方塊，可讓使用者從調色盤選取色彩，並將自訂色彩加入該調色盤。</span><span class="sxs-lookup"><span data-stu-id="755c4-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="755c4-104">這是您在其他 Windows 應用程式中看到可選取色彩的相同對話方塊。</span><span class="sxs-lookup"><span data-stu-id="755c4-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="755c4-105">只要在 Windows 應用程式中使用這個控制項，便不需要設定自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="755c4-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="755c4-106">在對話方塊中選取的色彩中傳回<xref:System.Windows.Forms.ColorDialog.Color%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="755c4-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="755c4-107">如果<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>屬性設定為`false`、 」 定義自訂色彩 」 按鈕已停用，而且使用者是限制為預先定義的色彩調色盤中。</span><span class="sxs-lookup"><span data-stu-id="755c4-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="755c4-108">如果<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>屬性設定為`true`，使用者無法選取遞色的色彩。</span><span class="sxs-lookup"><span data-stu-id="755c4-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="755c4-109">若要顯示對話方塊中，您必須呼叫其<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="755c4-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755c4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="755c4-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="755c4-111">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="755c4-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="755c4-112">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="755c4-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="755c4-113">操作說明：變更 Windows Forms ColorDialog 元件的外觀</span><span class="sxs-lookup"><span data-stu-id="755c4-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
