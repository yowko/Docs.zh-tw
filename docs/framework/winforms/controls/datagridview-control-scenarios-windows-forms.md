---
title: DataGridView 控制項案例 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 52c448f21be056e6166334785943356039baf3ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175288"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView 控制項案例 (Windows Form)
使用<xref:System.Windows.Forms.DataGridView>控制項，您可以顯示各種資料來源的表格式資料。 如需簡單的用法，您可以手動填入<xref:System.Windows.Forms.DataGridView>和操作直接透過控制項的資料。 一般而言，不過，您會將資料儲存在外部資料來源並將控制項繫結至其透過<xref:System.Windows.Forms.BindingSource>元件。  
  
 本主題描述一些常見案例涉及<xref:System.Windows.Forms.DataGridView>控制項。  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>案例 1:顯示少量的資料  
 您不必將資料儲存在外部資料來源將它顯示在<xref:System.Windows.Forms.DataGridView>控制項。 如果您正在使用少量的資料，您可以自行填入控制項，並管理透過控制項的資料。 這就叫做*režim bez vazby*。 如需詳細資訊，請參閱[如何：建立未繫結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   在未繫結模式中，您可以手動填入控制項。  
  
-   未繫結的模式是特別適用於少量的唯讀資料。  
  
-   未繫結的模式也適用於類似試算表或稀疏填入的資料表。  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>案例 2:檢視和更新儲存在外部資料來源中的資料  
 您可以使用<xref:System.Windows.Forms.DataGridView>做為使用者介面 (UI) 控制哪些使用者可以透過存取保留在資料來源，例如資料庫資料表或商務物件的集合中的資料。 如需詳細資訊，請參閱[如何：資料繫結至 Windows Form DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   繫結的模式可讓您連接到資料來源、 自動產生資料行是根據資料來源屬性或資料庫資料行，以及自動填入控制項。  
  
-   繫結的模式很適合大量的使用者與資料互動。 可以格式化資料以供顯示，以及使用者指定的資料可以剖析成資料來源所預期的格式。 可以偵測格式錯誤和資料庫條件約束錯誤的資料項目，以便可以警告使用者，且可以更正錯誤的儲存格。  
  
-   其他功能，例如資料行排序，凍結和重新調整順序可以讓使用者在其工作流程最簡便的方式檢視資料。  
  
-   剪貼簿支援可讓使用者將資料複製到其他應用程式的應用程式。  
  
## <a name="scenario-3-advanced-data"></a>案例 3:進階的資料  
 如果您有標準資料繫結模型不能解決的特殊需求，您可以藉由實作來管理控制項和您的資料之間的互動*虛擬模式*。 需要實作虛擬模式表示實作一或多個事件處理常式，可讓控制項要求的相關資訊的儲存格的資訊。  
  
 例如，如果您使用大量資料時，您可能想要實作虛擬模式，以確保最佳的效率。 虛擬模式也適合用於維護，以及從另一個資料來源擷取的資料行顯示未繫結資料行的值。  
  
 如需有關虛擬模式的詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   虛擬模式很適合您要微調效能時，顯示非常大量的資料。  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>案例 4:自動調整資料列和資料行的大小  
 當您顯示會定期更新的資料時，您可以自動調整資料列和資料行以確保所有內容都是可見。 <xref:System.Windows.Forms.DataGridView>控制項提供數個選項，可讓您啟用或停用手動調整大小、 調整大小以程式設計方式在特定時間，或調整大小自動每當內容變更。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   手動調整大小，可讓使用者調整儲存格的高度和寬度。  
  
-   自動調整大小，可讓您維護儲存格的大小，以便儲存格內容永遠不會被裁剪。  
  
-   以程式設計方式調整大小，可讓您調整儲存格大小以避免連續的自動調整大小的效能負面影響的特定時間。  
  
## <a name="scenario-5-simple-customization"></a>案例 5:簡單的自訂  
 <xref:System.Windows.Forms.DataGridView>控制項提供許多方式來改變其基本外觀和行為。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> 物件可讓您提供色彩、 字型、 格式和多個層級和個別的項目控制項的位置資訊。  
  
-   儲存格樣式可以分層和共用的多個項目，可讓您重複使用程式碼。  
  
## <a name="scenario-6-advanced-customization"></a>案例 6:進階的自訂  
 <xref:System.Windows.Forms.DataGridView>控制項提供許多的方式，供您自訂其外觀和行為。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   您可以提供自己的儲存格的繪製程式碼。 如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)。  
  
-   您可以提供您自己的資料列繪製。 這是很有用，例如，具有跨越多個資料行的內容中建立資料列。 如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)。  
  
-   您可以實作您自己的儲存格和資料行的類別，以自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：自訂資料格資料行中的 Windows Form DataGridView 控制項和擴充其行為和外觀](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。  
  
-   您可以實作您自己的儲存格和資料行的類別，來提供的內建的資料行類型以外的主控制項。 如需詳細資訊，請參閱[如何：Windows Forms DataGridView 儲存格主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)
