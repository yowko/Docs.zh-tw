---
title: 作法：在 MenuStrip 中顯示選項按鈕 (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971931"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>作法：在 MenuStrip 中顯示選項按鈕 (Windows Forms)

選項按鈕 (也稱為選項按鈕) 類似于核取方塊, 不同之處在于使用者一次只能選取一個。 雖然<xref:System.Windows.Forms.ToolStripMenuItem>類別預設不提供選項按鈕行為, 但類別確實提供了核取方塊行為, 可讓您自訂以實作為<xref:System.Windows.Forms.MenuStrip>控制項中功能表項目的選項按鈕行為。

當功能表<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>項的屬性為`true`時, 使用者可以按一下專案, 以切換核取記號的顯示。 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性會指出專案的目前狀態。 若要執行基本按鈕的行為, 您必須確定在選取專案時, 將先前選取之專案<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的屬性設為。 `false`

下列程式描述如何在繼承<xref:System.Windows.Forms.ToolStripMenuItem>類別的類別中, 執行這個和其他功能。 類別會覆寫成員<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> (例如<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>和), 以提供選項按鈕的選取行為和外觀。 `ToolStripRadioButtonMenuItem` 此外, 這個類別會覆<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>寫屬性, 因此除非選取父專案, 否則子功能表上的選項會停用。

## <a name="to-implement-option-button-selection-behavior"></a>若要執行選項按鈕選取行為

1. 將屬性初始化為`true` , 以啟用專案選取。 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>方法, 以在選取新專案時清除先前選取專案的選取範圍。

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>方法, 以確保按一下已選取的專案將不會清除選取範圍。

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>修改選項按鈕專案的外觀

1. 使用類別, 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法以將預設核取記號取代為<xref:System.Windows.Forms.RadioButtonRenderer>選項按鈕。

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>覆寫、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>和方法<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> 來追蹤滑鼠的狀態,並確保方法繪製正確的<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>選項按鈕狀態。

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>當未選取父專案時, 停用子功能表上的選項

1. `false` <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true` <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>覆寫屬性,如此一來,當專案具有值為且值為的父專案時,就會停用該專案。<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>方法以訂閱父專案的事件。

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. 在父專案<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件的處理常式中, 使專案失效, 以新啟用的狀態更新顯示。

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>範例

下列程式碼範例提供完整`ToolStripRadioButtonMenuItem`的類別, 以及用<xref:System.Windows.Forms.Form>來示範選項按鈕行為的類別和`Program`類別。

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- System、System.Drawing 和 System.Windows.Forms 組件的參考。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
- [如何：執行自訂 ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
