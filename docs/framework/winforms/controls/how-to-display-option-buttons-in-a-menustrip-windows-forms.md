---
title: HOW TO：在 MenuStrip (Windows Form) 中的顯示選項按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 61feda3f49c9a9e03a606c0284629f809d6876b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115527"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="2dd5e-102">HOW TO：在 MenuStrip (Windows Form) 中的顯示選項按鈕</span><span class="sxs-lookup"><span data-stu-id="2dd5e-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="2dd5e-103">選項按鈕，也稱為選項按鈕，如下核取方塊，不同之處在於使用者只能選取一個一次。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="2dd5e-104">雖然預設<xref:System.Windows.Forms.ToolStripMenuItem>類別不會提供選項按鈕的行為，但是類別提供核取方塊的行為，您可以自訂實作的功能表項目中的選項按鈕行為<xref:System.Windows.Forms.MenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="2dd5e-105">當<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>功能表項目的屬性是`true`，使用者可以按一下要切換顯示核取記號的項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="2dd5e-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性會指出項目的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="2dd5e-107">若要實作基本的選項按鈕的行為，您必須確定選取的項目時，您將設定<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>先前選取的項目屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="2dd5e-108">下列程序描述如何實作此繼承的類別中的其他功能<xref:System.Windows.Forms.ToolStripMenuItem>類別。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="2dd5e-109">`ToolStripRadioButtonMenuItem`類別會覆寫成員這類<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>和<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>提供的選取行為和外觀選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="2dd5e-110">此外，此類別會覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，因此，子功能表上的選項會停用，除非選取父項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="2dd5e-111">若要實作選項按鈕選取行為</span><span class="sxs-lookup"><span data-stu-id="2dd5e-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="2dd5e-112">初始化<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設`true`允許項目選取。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="2dd5e-113">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>方法，以選取新的項目時，清除先前選取的項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="2dd5e-114">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>方法，以確保該按一下已經選取的項目將不會清除選取項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="2dd5e-115">若要修改的選項按鈕的項目外觀</span><span class="sxs-lookup"><span data-stu-id="2dd5e-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="2dd5e-116">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法，以使用選項按鈕取代預設核取記號<xref:System.Windows.Forms.RadioButtonRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="2dd5e-117">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>，以及<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>方法來追蹤的滑鼠狀態，並且確定<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法來繪製正確的選項按鈕的狀態。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="2dd5e-118">若要停用選項 子功能表上的，未選取父項目時</span><span class="sxs-lookup"><span data-stu-id="2dd5e-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="2dd5e-119">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，讓它具有與父項目時，會停用項目<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>的值`true`並<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的值`false`。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="2dd5e-120">覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>方法，以訂閱<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件與父項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="2dd5e-121">在父項目的處理常式<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件，使其失效要以新的啟用狀態更新顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="2dd5e-122">範例</span><span class="sxs-lookup"><span data-stu-id="2dd5e-122">Example</span></span>  
 <span data-ttu-id="2dd5e-123">下列程式碼範例提供完整`ToolStripRadioButtonMenuItem`類別，以及<xref:System.Windows.Forms.Form>類別和`Program`類別，以示範選項按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2dd5e-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2dd5e-124">Compiling the Code</span></span>  
 <span data-ttu-id="2dd5e-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2dd5e-125">This example requires:</span></span>  
  
-   <span data-ttu-id="2dd5e-126">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2dd5e-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd5e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd5e-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="2dd5e-128">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="2dd5e-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="2dd5e-129">HOW TO：實作自訂的 ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="2dd5e-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
