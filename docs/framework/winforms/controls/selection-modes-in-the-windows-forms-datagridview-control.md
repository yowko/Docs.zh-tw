---
title: "Windows Form DataGridView 控制項中的選取模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0d605b7ee7e48ad0ed2e693f0e71e5f1c25e022
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的選取模式
有時候您想要根據使用者選取項目內執行動作的應用程式<xref:System.Windows.Forms.DataGridView>控制項。 根據動作，您可以限制選取的可能類型。 例如，假設您的應用程式可以列印報表，以針對目前選取的記錄。 在此情況下，您可能想要設定<xref:System.Windows.Forms.DataGridView>控制項，以便一律任意處按一下資料列內選取整個資料列，並因此選取一次該只有一個資料列。  
  
 您可以指定允許藉由設定的選取項目<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性，以下列其中一種<xref:System.Windows.Forms.DataGridViewSelectionMode>列舉值。  
  
|DataGridViewSelectionMode 值|描述|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|按一下儲存格選取它。 資料列和資料行標頭不能用於選取項目。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|按一下儲存格選取它。 按一下資料行標頭選取整個資料行。 資料行標頭不能用來排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|按一下資料格或是資料行的標頭選取整個資料行。 資料行標頭不能用來排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|按一下資料格或是資料列的標頭選取整個資料列。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|預設的選取模式。 按一下儲存格選取它。 按一下資料列標頭選取整個資料列。|  
  
> [!NOTE]
>  在執行階段變更選取模式，會自動清除目前的選取範圍。  
  
 根據預設，使用者可以選取多個資料列、 資料行或儲存格使用滑鼠拖曳時擴充或修改選取項目中，選取，或按一下左上方標題儲存格，即可選取所有的資料格控制項中按 CTRL 或 shift 鍵。 若要避免這種行為，將<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性`false`。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>和<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>模式允許使用者選取它們，然後按下 DELETE 鍵刪除資料列。 使用者可以刪除資料列，目前儲存格不是處於編輯模式時，才<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>屬性設定為`true`，並且基礎資料來源支援的使用者導向資料列刪除。 請注意，這些設定不會導致無法以程式設計方式的資料列刪除。  
  
## <a name="programmatic-selection"></a>以程式設計方式選取項目  
 目前的選取模式會限制以程式設計方式選取項目，以及使用者選取的行為。 您可以藉由設定，以程式設計方式變更目前的選取範圍`Selected`屬性的任何資料格、 資料列或資料行存在於<xref:System.Windows.Forms.DataGridView>控制項。 您也可以透過控制項中選取所有儲存格<xref:System.Windows.Forms.DataGridView.SelectAll%2A>方法，會根據選取模式。 若要清除選取項目，請使用<xref:System.Windows.Forms.DataGridView.ClearSelection%2A>方法。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性設定為`true`，您可以加入<xref:System.Windows.Forms.DataGridView>項目或變更從選取範圍移除這些`Selected`元素的屬性。 否則，設定`Selected`屬性`true`的一個項目會自動從選取範圍移除其他項目。  
  
 請注意，變更的值<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性不會變更目前的選取範圍。  
  
 您可以擷取目前選取的資料格、 資料列或透過資料行的集合<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>， <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>，和<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項。 選取控制項中的每個資料格時，存取這些屬性是沒有效率。 若要在此情況下避免對效能帶來負面影響，請使用<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>方法第一次。 此外，存取這些集合，以決定選取的資料格數目，資料列或資料行可能會沒有效率。 相反地，您應該使用<xref:System.Windows.Forms.DataGridView.GetCellCount%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>，或<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>方法，傳入<xref:System.Windows.Forms.DataGridViewElementStates.Selected>值。  
  
> [!TIP]
>  範例程式碼，示範如何以程式設計方式使用選取的資料格位於<xref:System.Windows.Forms.DataGridView>類別概觀。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [操作說明：設定 Windows Forms DataGridView 控制項的選取模式](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
