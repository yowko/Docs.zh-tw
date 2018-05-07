---
title: 疑難排解 DataRepeater 控制項 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 092bbe89bb73a40dee7161f014d40a581b0ddc06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>疑難排解 DataRepeater 控制項 (Visual Studio)
本主題列出常見的問題，當您正在使用時，可能會發生<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>不引發 DataRepeater 鍵盤和滑鼠事件  
 某些<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項事件，例如鍵盤和滑鼠事件，則不會引發。 這是依設計的結果。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身是容器<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>物件，並在執行階段無法存取。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不會在設計階段中公開事件。 因此，按一下項目或項目有焦點時按下按鍵不會引發事件。  
  
 這個例外狀況時，<xref:System.Windows.Forms.Control.Padding%2A>屬性會設定為大一點的值，以公開邊緣<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 在此情況下，按一下公開的邊界會引發滑鼠事件。  
  
 若要解決此問題，請加入<xref:System.Windows.Forms.Panel>控制權傳輸至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>區段<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，然後再加入剩餘的控制項加入<xref:System.Windows.Forms.Panel>。 然後，您可以加入程式碼以<xref:System.Windows.Forms.Panel>控制項的鍵盤和滑鼠事件的事件處理常式。  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater 部分藏繫結導覽  
 當您第一次加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項加入表單，並將資料繫結控制項，從**資料來源**視窗中，<xref:System.Windows.Forms.BindingNavigator>控制項可能會出現在最上層的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 這是已知的限制**資料來源**視窗，與保持一致的行為的其他控制項，例如<xref:System.Windows.Forms.DataGridView>控制項。  
  
 您可以移動任一<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>低於<xref:System.Windows.Forms.BindingNavigator>控制在設計階段，或加入程式碼中的下列類似一個框住`Load`事件處理常式。  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>控制項無法正確顯示在執行階段  
 在某些控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可能不在執行階段如預期般顯示。 處理序用來複製控制項從<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>永遠無法判斷所有控制項的所有屬性。 比方說，如果您加入未繫結<xref:System.Windows.Forms.ListBox>控制權傳輸至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制在設計階段，並擴展其<xref:System.Windows.Forms.ListBox.Items%2A>清單的字串集合，<xref:System.Windows.Forms.ListBox>空白，在將執行階段。 這是因為在複製程序無法納入考量<xref:System.Windows.Forms.ListBox.Items%2A>屬性。  
  
 您可以還原中遺漏的屬性，以修正問題，例如這<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>預設複製完成之後，就會發生的事件。 下列範例示範如何修復<xref:System.Windows.Forms.ListBox.Items%2A>集合<xref:System.Windows.Forms.ListBox>控制<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>事件處理常式。  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>遺漏項目標題的選取項目符號  
 當您變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性中的項目標頭<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，某些色彩選項可能會造成選取項目符號會消失。 變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性可能也會造成選取項目符號會消失。  
  
 無法變更的色彩和大小的選取項目符號。  
  
-   如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示第一次選取項目。  
  
-   如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.Black%2A>，選取項目符號選取控制項時，和鉛筆符號將不會顯示當控制項處於編輯模式時，將無法看到。  
  
-   如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標頭中的標記符號。  
  
 您可以使用，以提供您自己的項目標頭和選取項目符號<xref:System.Windows.Forms.PictureBox>控制和監視<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>屬性<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示未繫結的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [操作說明：搜尋 DataRepeater 控制項中的資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
