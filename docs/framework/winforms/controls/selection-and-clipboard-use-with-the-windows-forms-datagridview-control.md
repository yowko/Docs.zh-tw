---
title: 選取範圍和剪貼簿與 DataGridView 控制項搭配使用
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 6993f77e8ce532d8df1bdc7e6b6abc1cc3268e49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743058"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a>選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用
`DataGridView` 控制項提供各種選項，讓您設定使用者可以如何選取資料格、資料列和資料行。 例如，您可以啟用單一或多個選取範圍、當使用者按一下資料格時選取整個資料列或資料行，或是只有在使用者按一下標題時才選取整個資料列或資料行，這也會啟用資料格選取。 如果您想要提供您自己的使用者介面來進行選取，您可以停用一般選取專案，並以程式設計方式處理所有選取專案。 此外，您可以讓使用者將選取的值複製到剪貼簿。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)  
 描述控制項中使用者和以程式設計方式選取的選項。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的選取模式](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 描述如何設定當使用者按一下資料格時，單一資料列選取範圍的控制項。  
  
 [操作說明：取得 Windows Forms DataGridView 控制項中選取的儲存格、資料列和資料行](selected-cells-rows-and-columns-datagridview.md)  
 描述如何使用選取的儲存格、資料列和資料行集合。  
  
 [操作說明：讓使用者從 Windows Forms DataGridView 控制項將多個儲存格複製到剪貼簿](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 說明如何在控制項中啟用剪貼簿支援。  
  
## <a name="reference"></a>參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 提供 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性的參考檔。  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 提供 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> 屬性的參考檔。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> 類別的參考檔。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> 類別的參考檔。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> 類別的參考檔。  
  
## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
