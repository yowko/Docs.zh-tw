---
title: 如何：在 MenuStrip 中顯示選項按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735521"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="fdc39-102">如何：在 MenuStrip 中顯示選項按鈕 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="fdc39-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="fdc39-103">選項按鈕（也稱為選項按鈕）類似于核取方塊，不同之處在于使用者一次只能選取一個。</span><span class="sxs-lookup"><span data-stu-id="fdc39-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="fdc39-104">雖然 <xref:System.Windows.Forms.ToolStripMenuItem> 類別預設不提供選項按鈕行為，但類別確實提供了核取方塊行為，可讓您自訂以在 <xref:System.Windows.Forms.MenuStrip> 控制項中執行功能表項目的選項按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="fdc39-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="fdc39-105">`true`功能表項目的 [<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>] 屬性時，使用者可以按一下專案來切換核取記號的顯示。</span><span class="sxs-lookup"><span data-stu-id="fdc39-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="fdc39-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性會指出專案的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="fdc39-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="fdc39-107">若要執行基本按鈕的行為，您必須確定在選取專案時，將先前選取之專案的 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="fdc39-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="fdc39-108">下列程式描述如何在繼承 <xref:System.Windows.Forms.ToolStripMenuItem> 類別的類別中，執行這個和其他功能。</span><span class="sxs-lookup"><span data-stu-id="fdc39-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="fdc39-109">`ToolStripRadioButtonMenuItem` 類別會覆寫成員（例如 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> 和 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>），以提供選項按鈕的選取行為和外觀。</span><span class="sxs-lookup"><span data-stu-id="fdc39-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="fdc39-110">此外，這個類別會覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性，因此除非選取父專案，否則子功能表上的選項會停用。</span><span class="sxs-lookup"><span data-stu-id="fdc39-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="fdc39-111">若要執行選項按鈕選取行為</span><span class="sxs-lookup"><span data-stu-id="fdc39-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="fdc39-112">將 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 屬性初始化為 `true`，以啟用專案選取。</span><span class="sxs-lookup"><span data-stu-id="fdc39-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="fdc39-113">覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> 方法，以在選取新專案時清除先前選取專案的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="fdc39-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="fdc39-114">覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> 方法，以確保按一下已選取的專案將不會清除選取範圍。</span><span class="sxs-lookup"><span data-stu-id="fdc39-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="fdc39-115">修改選項按鈕專案的外觀</span><span class="sxs-lookup"><span data-stu-id="fdc39-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="fdc39-116">使用 <xref:System.Windows.Forms.RadioButtonRenderer> 類別，覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> 方法，將預設的核取記號取代為選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="fdc39-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="fdc39-117">覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>和 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> 方法以追蹤滑鼠的狀態，並確保 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> 方法繪製正確的選項按鈕狀態。</span><span class="sxs-lookup"><span data-stu-id="fdc39-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="fdc39-118">當未選取父專案時，停用子功能表上的選項</span><span class="sxs-lookup"><span data-stu-id="fdc39-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="fdc39-119">覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性，如此一來，當專案具有具有 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 值 `true` 和 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 值 `false`的父項目時，就會停用該專案。</span><span class="sxs-lookup"><span data-stu-id="fdc39-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="fdc39-120">覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> 方法，以訂閱父專案的 <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="fdc39-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="fdc39-121">在父項 <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> 事件的處理常式中，使專案失效，以新的啟用狀態更新顯示。</span><span class="sxs-lookup"><span data-stu-id="fdc39-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="fdc39-122">範例</span><span class="sxs-lookup"><span data-stu-id="fdc39-122">Example</span></span>

<span data-ttu-id="fdc39-123">下列程式碼範例提供完整的 `ToolStripRadioButtonMenuItem` 類別，以及 <xref:System.Windows.Forms.Form> 類別和 `Program` 類別，以示範選項按鈕的行為。</span><span class="sxs-lookup"><span data-stu-id="fdc39-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="fdc39-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fdc39-124">Compiling the Code</span></span>

<span data-ttu-id="fdc39-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fdc39-125">This example requires:</span></span>

- <span data-ttu-id="fdc39-126">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="fdc39-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdc39-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="fdc39-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="fdc39-128">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="fdc39-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="fdc39-129">操作說明：實作自訂的 ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="fdc39-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
