---
title: 如何：在 MenuStrip 中顯示選項按鈕 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: da2bb7edceaf83aa5178618fd4098631d65a7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538024"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="b40da-102">如何：在 MenuStrip 中顯示選項按鈕 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b40da-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="b40da-103">選項按鈕，也稱為 「 選項按鈕的類似於核取方塊，不同之處在於使用者只能選取一個一次。</span><span class="sxs-lookup"><span data-stu-id="b40da-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="b40da-104">雖然預設<xref:System.Windows.Forms.ToolStripMenuItem>類別並未提供選項按鈕的行為，但是類別提供您可以自訂實作中功能表項目的選項按鈕行為的核取方塊行為<xref:System.Windows.Forms.MenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b40da-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="b40da-105">當<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>功能表項目的屬性是`true`，使用者可以按一下要切換的核取記號顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="b40da-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性會指出項目的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="b40da-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="b40da-107">若要實作基本的選項按鈕的行為，您必須確定選取的項目時，您將設定<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>先前選取的項目屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="b40da-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="b40da-108">下列程序說明如何實作這個繼承的類別中的其他功能<xref:System.Windows.Forms.ToolStripMenuItem>類別。</span><span class="sxs-lookup"><span data-stu-id="b40da-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="b40da-109">`ToolStripRadioButtonMenuItem`類別會覆寫成員例如<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>和<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>提供的選取項目行為和外觀選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="b40da-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="b40da-110">此外，這個類別會覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，好的子功能表上的選項會停用，除非選取父項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="b40da-111">若要實作的選項按鈕選取行為</span><span class="sxs-lookup"><span data-stu-id="b40da-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="b40da-112">初始化<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性`true`啟用項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="b40da-113">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>方法，以選取新的項目時，清除先前選取之項目的選取項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="b40da-114">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>方法，以確保按一下已經選取的項目將不會清除選取項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="b40da-115">若要修改的選項按鈕項目外觀</span><span class="sxs-lookup"><span data-stu-id="b40da-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="b40da-116">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法，以使用以取代選項按鈕的預設核取記號<xref:System.Windows.Forms.RadioButtonRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="b40da-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="b40da-117">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>，和<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>方法來追蹤滑鼠的狀態，並且確定<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法會繪製正確的選項按鈕的狀態。</span><span class="sxs-lookup"><span data-stu-id="b40da-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="b40da-118">若要停用子功能表上的選項，不選取父項目</span><span class="sxs-lookup"><span data-stu-id="b40da-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="b40da-119">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，讓它具有與這兩個父項目時，停用項目<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>值`true`和<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>值`false`。</span><span class="sxs-lookup"><span data-stu-id="b40da-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="b40da-120">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>方法來訂閱<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件與父項目。</span><span class="sxs-lookup"><span data-stu-id="b40da-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="b40da-121">父項目的處理常式中<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件，讓更新與新的啟用狀態顯示的項目失效。</span><span class="sxs-lookup"><span data-stu-id="b40da-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="b40da-122">範例</span><span class="sxs-lookup"><span data-stu-id="b40da-122">Example</span></span>  
 <span data-ttu-id="b40da-123">下列程式碼範例提供完整`ToolStripRadioButtonMenuItem`類別，和<xref:System.Windows.Forms.Form>類別和`Program`類別來示範選項按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="b40da-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b40da-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b40da-124">Compiling the Code</span></span>  
 <span data-ttu-id="b40da-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b40da-125">This example requires:</span></span>  
  
-   <span data-ttu-id="b40da-126">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b40da-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40da-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b40da-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="b40da-128">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b40da-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="b40da-129">操作說明：實作自訂的 ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="b40da-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
