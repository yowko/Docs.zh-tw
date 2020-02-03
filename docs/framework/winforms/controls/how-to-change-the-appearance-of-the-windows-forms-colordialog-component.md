---
title: 變更 ColorDialog 元件的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746644"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="19dc0-102">如何：變更 Windows Form ColorDialog 元件的外觀</span><span class="sxs-lookup"><span data-stu-id="19dc0-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="19dc0-103">您可以使用多個屬性來設定 Windows Forms <xref:System.Windows.Forms.ColorDialog> 元件的外觀。</span><span class="sxs-lookup"><span data-stu-id="19dc0-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="19dc0-104">對話方塊有兩個區段：一個顯示基本色彩，另一個則可讓使用者定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="19dc0-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="19dc0-105">大部分的屬性會限制使用者可以從對話方塊中選取的色彩。</span><span class="sxs-lookup"><span data-stu-id="19dc0-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="19dc0-106">如果 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>] 屬性設定為 [`true`]，則允許使用者定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="19dc0-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="19dc0-107">如果對話方塊已展開以定義自訂色彩，則會 `true` [<xref:System.Windows.Forms.ColorDialog.FullOpen%2A>] 屬性;否則，使用者必須按一下 [定義自訂色彩] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19dc0-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="19dc0-108">當 [<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>] 屬性設定為 [`true`] 時，對話方塊會顯示一組基本色彩中的所有可用色彩。</span><span class="sxs-lookup"><span data-stu-id="19dc0-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="19dc0-109">如果 [<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 屬性設為 [`true`]，使用者就無法選取遞色色彩;只有純色可供選取。</span><span class="sxs-lookup"><span data-stu-id="19dc0-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="19dc0-110">如果 [<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>] 屬性設定為 [`true`]，則對話方塊上會出現 [說明] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19dc0-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="19dc0-111">當使用者按一下 [說明] 按鈕時，就會引發 <xref:System.Windows.Forms.ColorDialog> 元件的 <xref:System.Windows.Forms.CommonDialog.HelpRequest> 事件。</span><span class="sxs-lookup"><span data-stu-id="19dc0-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="19dc0-112">設定 [色彩] 對話方塊的外觀</span><span class="sxs-lookup"><span data-stu-id="19dc0-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="19dc0-113">將 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>]、[<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>]、[<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 和 [<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>] 屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="19dc0-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="19dc0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19dc0-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="19dc0-115">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="19dc0-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="19dc0-116">ColorDialog 元件概觀</span><span class="sxs-lookup"><span data-stu-id="19dc0-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
