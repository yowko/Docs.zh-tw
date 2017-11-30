---
title: "DataGridView 控制項案例 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 919197d8fdb40f0e0fb7b91fecae38f4e0e061bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView 控制項案例 (Windows Form)
與<xref:System.Windows.Forms.DataGridView>控制項，您可以顯示各種資料來源的表格式資料。 簡單的用途，您可以手動填入<xref:System.Windows.Forms.DataGridView>和操作直接透過控制項的資料。 一般而言，不過，會將資料儲存在外部資料來源，然後將控制項繫結，透過<xref:System.Windows.Forms.BindingSource>元件。  
  
 本主題描述一些常見的案例涉及<xref:System.Windows.Forms.DataGridView>控制項。  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>案例 1： 顯示少量的資料  
 您沒有將資料儲存在外部資料來源，以顯示在<xref:System.Windows.Forms.DataGridView>控制項。 如果您正在使用少量的資料，您可以自行填入控制項，並管理透過控制項的資料。 這稱為*未繫結的模式*。 如需詳細資訊，請參閱[How to： 建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   在未繫結模式中，您手動填入控制項。  
  
-   尤其適用於小量的唯讀資料繫結的模式。  
  
-   未繫結的模式也適用於類似試算表或沒有嚴密填入的資料表。  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>案例 2： 檢視和更新儲存在外部資料來源中的資料  
 您可以使用<xref:System.Windows.Forms.DataGridView>作為的使用者介面 (UI) 控制哪些使用者可以透過存取資料保留在資料來源，例如資料庫資料表或商務物件的集合。 如需詳細資訊，請參閱[How to： 將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   繫結的模式可讓您連接到資料來源、 自動產生資料行是根據資料來源屬性或資料庫資料行，以及自動填入控制項。  
  
-   繫結的模式適用於大量的使用者與資料互動。 可以格式化資料以供顯示，並指定使用者的資料可以剖析成資料來源所預期的格式。 如此可以警告使用者，可以更正錯誤的儲存格，可以偵測到資料輸入格式錯誤和資料庫條件約束錯誤。  
  
-   其他功能，例如資料行排序，凍結和重新調整順序可以讓使用者在其工作流程最簡便的方式檢視資料。  
  
-   剪貼簿支援可讓使用者複製到其他應用程式的應用程式中的資料。  
  
## <a name="scenario-3-advanced-data"></a>案例 3： 進階的資料  
 如果您有標準的資料繫結模型將不會處理的特殊需求，您可以藉由實作來管理控制項和資料之間的互動*虛擬模式*。 需要實作虛擬模式表示實作一或多個事件處理常式，讓控制項要求有關資料格的資訊一樣重要。  
  
 例如，如果您使用大量的資料時，您可以實作虛擬模式，以確保最佳的效率。 虛擬模式也可用於維護，以及從另一個資料來源擷取的資料行顯示未繫結資料行的值。  
  
 如需虛擬模式的詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   虛擬模式適用於您要微調效能時，顯示非常大量的資料。  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>案例 4： 自動調整資料列和資料行  
 當您顯示經常更新的資料時，您可以自動調整資料列和資料行以確保所有內容都都可見。 <xref:System.Windows.Forms.DataGridView>控制項提供數個選項，可讓您啟用或停用手動調整大小，在特定時間，以程式設計方式調整或調整大小自動每當內容變更。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   手動調整大小，可讓使用者調整儲存格的高度和寬度。  
  
-   自動調整大小，可讓您以維護儲存格的大小，讓儲存格內容永遠不會被截斷。  
  
-   以程式設計方式調整大小，可讓您調整儲存格大小以避免持續自動調整大小的效能負面影響的特定時間。  
  
## <a name="scenario-5-simple-customization"></a>案例 5： 簡單的自訂  
 <xref:System.Windows.Forms.DataGridView>控制項提供許多方式來改變其基本外觀和行為。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle>物件可讓您提供色彩、 字型格式及多個層級和個別的項目控制項的位置資訊。  
  
-   儲存格樣式可以分層和多個項目，讓您重複使用程式碼共用。  
  
## <a name="scenario-6-advanced-customization"></a>案例 6： 進階的自訂  
 <xref:System.Windows.Forms.DataGridView>控制項提供許多方式，讓您自訂其外觀和行為。  
  
### <a name="scenario-key-points"></a>案例重點  
  
-   您可以提供您自己的儲存格繪製程式碼。 如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)。  
  
-   您可以提供您自己的資料列繪製。 這是很有用，例如，以跨越多個資料行的內容中建立資料列。 如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的資料列外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)。  
  
-   您可以實作您自己的儲存格和資料行的類別，以自訂儲存格的外觀。 如需詳細資訊，請參閱[How to： 自訂資料格和擴充其行為和外觀的 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。  
  
-   您可以實作您自己的儲存格和資料行的類別，以提供的內建的資料行類型以外的主控制項。 如需詳細資訊，請參閱[How to： 在 Windows Form DataGridView 儲存格的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
