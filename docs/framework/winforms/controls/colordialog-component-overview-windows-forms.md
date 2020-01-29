---
title: ColorDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736960"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="c0e5c-102">ColorDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="c0e5c-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="c0e5c-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> 元件是預先設定的對話方塊，可讓使用者從調色板選取色彩，並將自訂色彩新增至該色板。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="c0e5c-104">這是您在其他 Windows 應用程式中看到可選取色彩的相同對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="c0e5c-105">只要在 Windows 應用程式中使用這個控制項，便不需要設定自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="c0e5c-106">在對話方塊中選取的色彩會在 <xref:System.Windows.Forms.ColorDialog.Color%2A> 屬性中傳回。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="c0e5c-107">如果 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>] 屬性設定為 [`false`]，則會停用 [定義自訂色彩] 按鈕，並將使用者限制為調色板中預先定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="c0e5c-108">如果 [<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 屬性設定為 [`true`]，使用者就無法選取遞色。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="c0e5c-109">若要顯示對話方塊，您必須呼叫其 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c0e5c-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e5c-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0e5c-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="c0e5c-111">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="c0e5c-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="c0e5c-112">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="c0e5c-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="c0e5c-113">如何：變更 Windows Forms ColorDialog 元件的外觀</span><span class="sxs-lookup"><span data-stu-id="c0e5c-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
