---
title: HOW TO：錨定和停駐 FlowLayoutPanel 控制項中的子控制項
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 255ac50ae79d6931c9b82b50677c450c0834fdea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011184"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>HOW TO：錨定和停駐 FlowLayoutPanel 控制項中的子控制項
<xref:System.Windows.Forms.FlowLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>錨定和停駐 FlowLayoutPanel 控制項中的子控制項  
  
1. 請在表單上建立 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
2. 設定<xref:System.Windows.Forms.Control.Width%2A>的<xref:System.Windows.Forms.FlowLayoutPanel>若要控制**300**，並設定其<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>至<xref:System.Windows.Forms.FlowDirection.TopDown>。  
  
3. 建立兩個 <xref:System.Windows.Forms.Button> 控制項，並置入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
4. 設定<xref:System.Windows.Forms.Control.Width%2A>的第一個按鈕**200**。  
  
5. 將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
    > [!NOTE]
    >  第二個按鈕會假設與第一個按鈕的寬度相同。 它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。  
  
6. 將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 `None`。 這會使按鈕假設為原始的寬度。  
  
7. 將第二個按鈕的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設為 `Left, Right`。  
  
    > [!IMPORTANT]
    >  第二個按鈕會假設與第一個按鈕的寬度相同。 它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。 這是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項錨定和停駐的一般規則：對於垂直流動方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會計算資料行中最寬子控制項的隱含資料行寬度。 此資料行中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的所有其他控制項會配合隱含資料行對齊或自動縮放。 此行為的運作方式類似水平流動方向。 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項由此資料列中最高子控制項的高度計算隱含資料列的高度，在此資料列中所有停駐或錨定的子控制項會配合隱含資料列對齊或調整大小。  
  
## <a name="example"></a>範例  
 下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.LeftToRight>。  
  
 ![FlowLayoutPanel 錨定](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.TopDown>。  
  
 ![FlowLayoutPanel 錨定](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 下列程式碼範例示範 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之不同的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值。  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel 控制項概觀](flowlayoutpanel-control-overview.md)
