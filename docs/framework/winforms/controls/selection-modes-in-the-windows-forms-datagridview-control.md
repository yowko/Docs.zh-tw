---
title: Windows Form DataGridView 控制項中的選取模式
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 79e13e65938252015e43b59a962d40f20963a5df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902664"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的選取模式
有時候您想要根據使用者選取項目內執行動作的應用程式<xref:System.Windows.Forms.DataGridView>控制項。 根據動作，您可能要限制可能的選取項目類型。 例如，假設您的應用程式可以列印報表，以針對目前選取的記錄。 在此情況下，您可能想要設定<xref:System.Windows.Forms.DataGridView>控制項，以便一律任意處按一下資料列中選取整個資料列，並因此可以選取一次該只有一個資料列。  
  
 您可以指定允許藉由設定的選取項目<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性，以下列其中一種<xref:System.Windows.Forms.DataGridViewSelectionMode>列舉值。  
  
|DataGridViewSelectionMode value|描述|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|按一下資料格會選取它。 資料列和資料行標頭不能用於選取項目。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|按一下資料格會選取它。 按一下資料行標頭選取整個資料行。 資料行標頭不能用於排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|按一下資料格或是資料行的標頭會選取整個資料行。 資料行標頭不能用於排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|按一下資料格或是資料列的標頭會選取整個資料列。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|預設的選取模式。 按一下資料格會選取它。 按一下資料列標頭選取整個資料列。|  
  
> [!NOTE]
>  在執行階段變更選取模式時，也將會自動清除目前的選取項目。  
  
 根據預設，使用者可以選取多個資料列、 資料行或資料格拖曳滑鼠時擴充或修改選取項目中，選取，或是按一下左上方的標題儲存格來選取所有儲存格控制項中按 CTRL 或 shift 鍵。 若要避免此行為，將<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性設`false`。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>和<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>模式允許使用者選取它們，然後按 DELETE 鍵刪除資料列。 使用者可以刪除資料列，只有在目前的儲存格不是處於編輯模式時，才<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>屬性設定為`true`，並且基礎資料來源支援使用者導向資料列刪除。 請注意，這些設定不會防止刪除以程式設計方式的資料列。  
  
## <a name="programmatic-selection"></a>以程式設計方式選取項目  
 目前的選取模式會限制以程式設計方式選取項目，以及使用者選取的行為。 您可以藉由設定，以程式設計方式變更目前的選取範圍`Selected`屬性的任何資料格、 資料列或資料行存在於<xref:System.Windows.Forms.DataGridView>控制項。 您也可以透過控制項中選取所有儲存格<xref:System.Windows.Forms.DataGridView.SelectAll%2A>方法，根據選取模式。 若要清除選取項目，請使用<xref:System.Windows.Forms.DataGridView.ClearSelection%2A>方法。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性設定為`true`，您可以新增<xref:System.Windows.Forms.DataGridView>項目或從選取範圍移除方法是變更`Selected`項目的屬性。 否則，請設定`Selected`屬性設`true`的一個項目會自動從選取範圍移除其他項目。  
  
 請注意，變更的值<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性不會更改目前的選取範圍。  
  
 您可以擷取目前選取的資料格、 資料列或資料行的集合<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>， <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>，並<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>的屬性<xref:System.Windows.Forms.DataGridView>控制項。 選取控制項中的每個資料格時，存取這些屬性是效率不佳。 若要在此情況下避免對效能帶來負面影響，請使用<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>方法第一次。 此外，存取這些集合，以決定選取之資料格數目，資料列或資料行可能會沒有效率。 因此，您應該改用<xref:System.Windows.Forms.DataGridView.GetCellCount%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>，或<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>方法並傳入<xref:System.Windows.Forms.DataGridViewElementStates.Selected>值。  
  
> [!TIP]
>  示範如何以程式設計方式使用所選儲存格的範例程式碼可在<xref:System.Windows.Forms.DataGridView>類別概觀。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [如何：設定 Windows Forms DataGridView 控制項的選取模式](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
