---
title: 如何：確認子資料表中選取的資料列保持在正確位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: e1fdb007451c157e60a1ad723b5d2d06bc85ecdf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135584"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>如何：確認子資料表中選取的資料列保持在正確位置
有時候當您使用 Windows Form 中的資料繫結時，您會在所謂父/子或主要/詳細資料檢視中顯示資料。 這是指來自相同來源的資料顯示在兩個控制項中的資料繫結案例。 在一個控制項中變更選取範圍會造成第二個控制項中顯示的資料也變更。 比方說，第一個控制項可能包含客戶清單，而第二個控制項包含與第一個控制項中所選取客戶相關的訂單清單。  
  
 從 .NET Framework 2.0 版開始，當您在父/子檢視中顯示資料時，您可能必須採取額外的步驟，以確定子資料表中目前選取的資料列不會重設為資料表的第一個資料列。 若要這樣做，您必須快取子系資料表位置並在父資料表變更之後重設它。 重設子系通常會發生在父資料表的資料列欄位第一次變更時。  
  
### <a name="to-cache-the-current-child-position"></a>快取目前的子系位置  
  
1.  宣告整數變數來儲存子系清單位置，並宣告布林值變數來儲存是否要快取子系位置。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  處理繫結 <xref:System.Windows.Forms.CurrencyManager> 的 <xref:System.Windows.Forms.CurrencyManager.ListChanged> 事件，並檢查 <xref:System.ComponentModel.ListChangedType.Reset> 的 <xref:System.ComponentModel.ListChangedType>。  
  
3.  檢查 <xref:System.Windows.Forms.CurrencyManager> 的目前位置。 如果大於清單中的第一個項目 (通常為 0)，將它儲存到變數。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  處理父貨幣管理員的父清單 <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> 事件。 在處理常式中，設定布林值以表示不是快取案例。 如果發生 <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged>，父系的變更是清單位置變更，而不是項目值變更。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>重設子系位置  
  
1.  處理子系繫結的 <xref:System.Windows.Forms.CurrencyManager> 的 <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> 事件。  
  
2.  將子資料表位置重設為儲存在先前程序中的快取位置。  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>範例  
 下列範例示範如何儲存子資料表在 <xref:System.Windows.Forms.CurrencyManager> 上的目前位置，並在父資料表上編輯完成之後重設位置。 此範例包含兩個 <xref:System.Windows.Forms.DataGridView> 控制項，它們已使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 <xref:System.Data.DataSet> 中的兩個資料表。 兩個資料表之間會建立關聯性，而關聯性則加入至 <xref:System.Data.DataSet>。 子資料表中的位置一開始會設為第三個資料列，以做為示範之用。  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 若要測試程式碼範例，請執行下列步驟：  
  
1.  執行範例。  
  
2.  確定已選取 [快取和重設位置] 核取方塊。  
  
3.  按一下 [清除父欄位] 按鈕，使父資料表的欄位變更。 請注意，子資料表中的選取資料列不會變更。  
  
4.  關閉並重新執行此範例。 您要執行這項操作，因為重設行為只會在父資料列中的第一次變更時發生。  
  
5.  清除 [快取和重設位置] 核取方塊。  
  
6.  按一下 [清除父欄位] 按鈕。 請注意，子資料表中的選取資料列會變更為第一個資料列。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing、System.Windows.Forms 和 System.XML 組件的參考。  
  
 如需如何針對 Visual Basic 或 Visual C# 建置此範例從命令列資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：確保繫結至相同資料來源的多個控制項都能保持同步](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [BindingSource 元件](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
