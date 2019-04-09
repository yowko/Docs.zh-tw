---
title: HOW TO：使用 TabControl 顯示側邊對齊的定位點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: ce0c7d48f053094d0026348fea8221ea80ccca59
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142892"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>HOW TO：使用 TabControl 顯示側邊對齊的定位點
<xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Alignment%2A> 屬性支援以垂直方式 (沿著控制項的左或右邊緣) 顯示索引標籤，而非水平方式 (橫跨控制項的頂端或底部) 。 根據預設，此垂直顯示會導致不良的使用者經驗，因為當啟用視覺化樣式時，<xref:System.Windows.Forms.TabPage> 物件的 <xref:System.Windows.Forms.TabPage.Text%2A> 屬性並不會在索引標籤中顯示。 也沒有直接控制索引標籤內文字方向的方式。您可以在 <xref:System.Windows.Forms.TabControl> 上面使用主控描繪，來改善這種經驗。  
  
 下列程序示範如何使用主控描繪功能來呈現靠右對齊的索引標籤，使索引標籤文字從左向右跑。  
  
### <a name="to-display-right-aligned-tabs"></a>若要顯示靠右對齊的索引標籤  
  
1.  加入 <xref:System.Windows.Forms.TabControl> 至您的表單。  
  
2.  將 <xref:System.Windows.Forms.TabControl.Alignment%2A> 屬性設定為 <xref:System.Windows.Forms.TabAlignment.Right>。  
  
3.  設定 <xref:System.Windows.Forms.TabControl.SizeMode%2A> 屬性為 <xref:System.Windows.Forms.TabSizeMode.Fixed>，好讓所有的索引標籤有相同寬度。  
  
4.  設定 <xref:System.Windows.Forms.TabControl.ItemSize%2A> 屬性為索引標籤的慣用固定大小。 請記住，<xref:System.Windows.Forms.TabControl.ItemSize%2A> 屬性的行為如同索引標籤已在頂端，儘管它們是靠右對齊的。 因此，為了讓索引標籤更寬，您必須變更 <xref:System.Drawing.Size.Height%2A> 屬性，而且為了讓它們更高，您必須變更 <xref:System.Drawing.Size.Width%2A> 屬性。  
  
     為了使下列程式碼範例獲得最佳結果，請設定索引標籤的 <xref:System.Drawing.Size.Width%2A> 為 25 ，並設定 <xref:System.Drawing.Size.Height%2A> 為 100。  
  
5.  將 <xref:System.Windows.Forms.TabControl.DrawMode%2A> 屬性設定為 <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>。  
  
6.  定義 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.DrawItem> 事件處理常式，這會從左到右呈現文字。  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [TabControl 控制項](tabcontrol-control-windows-forms.md)
