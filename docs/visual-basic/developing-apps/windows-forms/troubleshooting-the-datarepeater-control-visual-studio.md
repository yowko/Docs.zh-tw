---
title: 疑難排解 DataRepeater 控制項 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 7b045e1c45221cbde82c88286da8e698a763d844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580599"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>疑難排解 DataRepeater 控制項 (Visual Studio)
本主題列出常見的問題，您正在使用時可能發生<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>不會引發 DataRepeater 鍵盤和滑鼠事件  
 某些<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項事件，例如鍵盤和滑鼠事件，則不會引發。 這是依設計的結果。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身是容器<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>物件，並不能在執行階段存取。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不會在設計階段公開事件。 因此，按一下項目或項目有焦點時按下按鍵不會引發事件。  
  
 這個例外狀況時，<xref:System.Windows.Forms.Control.Padding%2A>屬性會設定為大一點的值，以公開 （expose） 的邊緣<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 在此情況下，公開界中按一下，會引發滑鼠事件。  
  
 若要解決此問題，請新增<xref:System.Windows.Forms.Panel>若要控制<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>一節<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，然後再新增至控制項的其餘部分<xref:System.Windows.Forms.Panel>。 然後，您可以加入程式碼以<xref:System.Windows.Forms.Panel>控制項的鍵盤和滑鼠事件的事件處理常式。  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater 部分隱藏在繫結導覽  
 當您第一次新增<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項加入表單，並再將資料繫結控制項，從新增**資料來源** 視窗中，<xref:System.Windows.Forms.BindingNavigator>控制項可能會出現頂端<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 這是已知的限制**資料來源**視窗和做法與行為的其他控制項，例如<xref:System.Windows.Forms.DataGridView>控制項。  
  
 您可以其中一個移動<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>低於<xref:System.Windows.Forms.BindingNavigator>控制在設計階段，或加入程式碼中的下列`Load`事件處理常式。  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>控制項無法正確顯示在執行階段  
 中的部分控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可能不會顯示，如預期般在執行階段。 用於複製從控制項的程序<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不總是能夠判斷的所有控制項的所有屬性。 例如，如果您加入未繫結<xref:System.Windows.Forms.ListBox>控制對<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在設計階段，並填入其<xref:System.Windows.Forms.ListBox.Items%2A>清單的字串集合，<xref:System.Windows.Forms.ListBox>在執行階段會空白。 這是因為複製程序無法納入考量<xref:System.Windows.Forms.ListBox.Items%2A>屬性。  
  
 您可以藉由還原中遺漏的屬性來修正這類問題<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>預設複製完成之後，就會發生的事件。 下列範例示範如何修復<xref:System.Windows.Forms.ListBox.Items%2A>的集合<xref:System.Windows.Forms.ListBox>控制中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>事件處理常式。  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>選取項目符號項目標題遺漏  
 當您變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性中的項目標頭<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，有些色彩選項可能會導致消失的選取項目符號。 變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性也可能會導致消失的選取項目符號。  
  
 無法變更選取項目符號的大小與色彩。  
  
-   如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示第一次選取項目。  
  
-   如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.Black%2A>，選取項目符號將不會顯示選取控制項，並使用鉛筆符號將不會顯示當控制項處於編輯模式。  
  
-   如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標題中的標記符號。  
  
 您可以使用，以提供您自己的項目標頭和選取項目符號<xref:System.Windows.Forms.PictureBox>控制和監視<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>屬性<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。  
  
## <a name="see-also"></a>另請參閱
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示未繫結的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [如何：變更 DataRepeater 控制項的版面配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [如何：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [如何：停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [如何：DataRepeater 控制項中的搜尋資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [如何：使用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
