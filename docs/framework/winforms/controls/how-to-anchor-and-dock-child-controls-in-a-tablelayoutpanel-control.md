---
title: 如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: eee67d739de13b125aa1eb8ee86de19ba645a2f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529093"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項
<xref:System.Windows.Forms.TableLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>若要對齊 TableLayoutPanel 儲存格中的子控制項  
  
1.  請在表單上建立 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
2.  值設定<xref:System.Windows.Forms.TableLayoutPanel>控制項的<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>和<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>屬性**1**。  
  
3.  在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中建立 <xref:System.Windows.Forms.Button> 控制項。 <xref:System.Windows.Forms.Button> 會佔用儲存格的左上角。  
  
4.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Left`。 <xref:System.Windows.Forms.Button> 控制項移到與儲存格左框線對齊。  
  
    > [!NOTE]
    >  此行為不同於其他容器控制項的行為。 在其他容器控制項中，當 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性被設定時，子控制項不會移動，而且當 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性被設定時，錨定的控制項與父容器界限之間的距離固定。  
  
5.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Left`。 <xref:System.Windows.Forms.Button> 控制項移到佔用儲存格左上角。  
  
6.  重複步驟 5 的值的`Top, Right`移動<xref:System.Windows.Forms.Button>儲存格右上角的控制項。 使用 `Bottom, Left` 和 `Bottom, Right` 值重複進行。  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>若要自動縮放 TableLayoutPanel 儲存格中的子控制項  
  
1.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Left, Right`。 會調整 <xref:System.Windows.Forms.Button> 控制項的大小，自動縮放整個儲存格。  
  
    > [!NOTE]
    >  此行為不同於其他容器控制項的行為。 在其他容器控制項中，子控制項不是調整大小的時機<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定為`Left, Right`或`Top, Bottom`。  
  
2.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Bottom`。 會調整 <xref:System.Windows.Forms.Button> 控制項的大小，從頂端到底部自動縮放儲存格。  
  
3.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Bottom, Left, Right`。 調整 <xref:System.Windows.Forms.Button> 控制項的大小以填滿儲存格。  
  
4.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `None`。 調整 <xref:System.Windows.Forms.Button> 控制項的大小，並在儲存格中置中。  
  
5.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值為 <xref:System.Windows.Forms.DockStyle.Left>。 <xref:System.Windows.Forms.Button> 控制項移到與儲存格左框線對齊。 會保留 <xref:System.Windows.Forms.Button> 控制項寬度，但會調整它高度的大小，以垂直方式填滿儲存格。  
  
    > [!NOTE]
    >  這與在其他容器控制項中發生的行為相同。  
  
6.  變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值為 <xref:System.Windows.Forms.DockStyle.Fill>。 調整 <xref:System.Windows.Forms.Button> 控制項的大小以填滿儲存格。  
  
## <a name="example"></a>範例  
 下圖顯示錨定在 5 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 資料格的 5 個按鈕。  
  
 ![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 下圖顯示錨定在 4 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 儲存格角落的 4 個按鈕。  
  
 ![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 下圖顯示藉由錨定在 3 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 儲存格來自動縮放 3 個按鈕。  
  
 ![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 下列程式碼範例示範所有 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值組合。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 建置此範例從 visual Basic 或 Visual C# 命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
