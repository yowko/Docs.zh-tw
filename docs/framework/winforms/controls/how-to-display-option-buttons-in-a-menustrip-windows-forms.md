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
ms.openlocfilehash: e764c7e181870d8faf6157cacc13164977ce2e3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306231"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>HOW TO：在 MenuStrip (Windows Form) 中的顯示選項按鈕
選項按鈕，也稱為選項按鈕，如下核取方塊，不同之處在於使用者只能選取一個一次。 雖然預設<xref:System.Windows.Forms.ToolStripMenuItem>類別不會提供選項按鈕的行為，但是類別提供核取方塊的行為，您可以自訂實作的功能表項目中的選項按鈕行為<xref:System.Windows.Forms.MenuStrip>控制項。  
  
 當<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>功能表項目的屬性是`true`，使用者可以按一下要切換顯示核取記號的項目。 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性會指出項目的目前狀態。 若要實作基本的選項按鈕的行為，您必須確定選取的項目時，您將設定<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>先前選取的項目屬性`false`。  
  
 下列程序描述如何實作此繼承的類別中的其他功能<xref:System.Windows.Forms.ToolStripMenuItem>類別。 `ToolStripRadioButtonMenuItem`類別會覆寫成員這類<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>和<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>提供的選取行為和外觀選項按鈕。 此外，此類別會覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，因此，子功能表上的選項會停用，除非選取父項目。  
  
### <a name="to-implement-option-button-selection-behavior"></a>若要實作選項按鈕選取行為  
  
1. 初始化<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設`true`允許項目選取。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>方法，以選取新的項目時，清除先前選取的項目選取項目。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>方法，以確保該按一下已經選取的項目將不會清除選取項目。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>若要修改的選項按鈕的項目外觀  
  
1. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法，以使用選項按鈕取代預設核取記號<xref:System.Windows.Forms.RadioButtonRenderer>類別。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>， <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>，以及<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>方法來追蹤的滑鼠狀態，並且確定<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法來繪製正確的選項按鈕的狀態。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>若要停用選項 子功能表上的，未選取父項目時  
  
1. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性，讓它具有與父項目時，會停用項目<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>的值`true`並<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的值`false`。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2. 覆寫<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>方法，以訂閱<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件與父項目。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3. 在父項目的處理常式<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>事件，使其失效要以新的啟用狀態更新顯示的項目。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>範例  
 下列程式碼範例提供完整`ToolStripRadioButtonMenuItem`類別，以及<xref:System.Windows.Forms.Form>類別和`Program`類別，以示範選項按鈕行為。  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
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
- [如何：實作自訂的 ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
