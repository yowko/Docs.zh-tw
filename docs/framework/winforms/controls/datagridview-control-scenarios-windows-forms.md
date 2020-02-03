---
title: DataGridView 控制項案例
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742468"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView 控制項案例 (Windows Form)
有了 <xref:System.Windows.Forms.DataGridView> 控制項，您就可以從各種資料來源顯示表格式資料。 針對簡單的用法，您可以手動填入 <xref:System.Windows.Forms.DataGridView>，並直接透過控制項運算元據。 不過，一般而言，您會將資料儲存在外部資料源，並透過 <xref:System.Windows.Forms.BindingSource> 元件將控制項系結至它。  
  
 本主題描述一些牽涉到 <xref:System.Windows.Forms.DataGridView> 控制項的常見案例。  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>案例1：顯示少量的資料  
 您不需要將資料儲存在外部資料源中，就能在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示。 如果您使用的資料量很少，您可以自行填入控制項，並透過控制項運算元據。 這稱為「*解除*系結模式」。 如需詳細資訊，請參閱[如何：建立未系結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- 在解除系結模式中，您會手動填入控制項。  
  
- 「解除系結模式」特別適用于少量的唯讀資料。  
  
- 解除系結模式也適用于類似試算表或稀疏的已填入資料表。  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>案例2：查看和更新儲存在外部資料源中的資料  
 您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項做為使用者介面（UI），讓使用者可以透過它存取資料來源中保留的資料，例如資料庫資料表或商務物件的集合。 如需詳細資訊，請參閱[如何：將資料系結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- 系結模式可讓您連接到資料來源、根據資料來源屬性或資料庫資料行自動產生資料行，以及自動填入控制項。  
  
- 系結模式適用于大量使用者與資料的互動。 資料可以針對顯示進行格式化，而且使用者指定的資料可以剖析成資料來源所預期的格式。 可以偵測到資料輸入格式錯誤和資料庫條件約束錯誤，讓使用者可以收到警告，而且可以更正錯誤的儲存格。  
  
- 其他功能（例如資料行排序、凍結和重新排列）可讓使用者以最方便的方式來查看其工作流程的資料。  
  
- 剪貼簿支援可讓使用者將資料從您的應用程式複製到其他應用程式。  
  
## <a name="scenario-3-advanced-data"></a>案例3： Advanced Data  
 如果您有標準資料系結模型無法解決的特殊需求，您可以藉由執行*虛擬模式*來管理控制項與資料之間的互動。 執行虛擬模式表示執行一或多個事件處理常式，可讓控制項要求資料格的相關資訊（如需要資訊）。  
  
 例如，如果您使用大量資料，您可能會想要執行虛擬模式以確保最佳的效率。 虛擬模式也很適合用來維護您所顯示的未系結資料行值，以及從另一個資料來源中取出的資料行。  
  
 如需虛擬模式的詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- 當您需要微調效能時，虛擬模式適合用來顯示非常大量的資料。  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>案例4：自動調整資料列和資料行的大小  
 當您顯示定期更新的資料時，您可以自動調整資料列和資料行的大小，以確保所有內容都是可見的。 <xref:System.Windows.Forms.DataGridView> 控制項提供數個選項，可讓您啟用或停用手動調整大小、在特定時間以程式設計方式調整大小，或在內容變更時自動調整大小。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- 手動調整大小可讓使用者調整儲存格的高度和寬度。  
  
- 自動調整大小可讓您維護資料格大小，讓資料格內容永遠不會被裁剪。  
  
- 以程式設計方式調整大小，可讓您在特定時間調整儲存格的大小，以避免連續自動調整的效能損失。  
  
## <a name="scenario-5-simple-customization"></a>案例5：簡單的自訂  
 <xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您改變其基本外觀和行為。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> 物件可讓您在多個層級，以及針對控制項的個別元素，提供色彩、字型、格式和位置資訊。  
  
- 儲存格樣式可以透過多個元素進行分層和共用，讓您重複使用程式碼。  
  
## <a name="scenario-6-advanced-customization"></a>案例6： Advanced 自訂  
 <xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您自訂其外觀和行為。  
  
### <a name="scenario-key-points"></a>案例重點  
  
- 您可以提供自己的儲存格繪製程式碼。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)。  
  
- 您可以提供自己的資料列繪製。 例如，如果要建立的資料列具有跨越多個資料行的內容，這就很有用。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)。  
  
- 您可以執行自己的儲存格和資料行類別，以自訂資料格外觀。 如需詳細資訊，請參閱[如何：藉由擴充其行為和外觀，自訂 Windows Forms DataGridView 控制項中的儲存格和資料行](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。  
  
- 除了內建資料行類型所提供的控制項外，您還可以將自己的儲存格和資料行類別實作為裝載控制項。 如需詳細資訊，請參閱[如何： Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)
