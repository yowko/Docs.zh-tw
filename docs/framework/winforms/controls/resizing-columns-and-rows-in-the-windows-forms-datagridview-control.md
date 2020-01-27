---
title: 調整 DataGridView 控制項中的資料行和資料列大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742407"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>調整 Windows Form DataGridView 控制項中的資料行和資料列的大小
`DataGridView` 控制項提供許多選項，可讓您自訂其資料行和資料列的調整大小行為。 一般來說，`DataGridView` 的資料格不會根據其內容調整大小。 相反地，它們會裁剪大於儲存格的任何顯示值。 如果內容可以顯示為字串，資料格就會顯示在工具提示中。  
  
 根據預設，使用者可以使用滑鼠拖曳資料列、資料行和標頭分隔線，以顯示詳細資訊。 使用者也可以按兩下分隔線，根據其內容自動調整相關列、資料行或標頭的大小。  
  
 `DataGridView` 控制項提供屬性、方法和事件，可讓您自訂或停用所有這些使用者導向的行為。 此外，您可以透過程式設計的方式調整資料列、資料行和標頭的大小，以符合其內容，或者您可以設定它們在內容變更時自動調整其大小。 您也可以將資料行設定為自動將控制項的可用寬度除以您指定的比例。  
  
## <a name="in-this-section"></a>本章節內容  
 [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)  
 描述調整資料列、資料行和標頭的選項。 也會提供有關調整大小相關屬性和方法的詳細資料，並說明常見的使用案例。  
  
 [Windows Forms DataGridView 控制項中的資料行填入模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 詳細描述資料行填滿模式，並提供示範程式碼，可讓您用來試驗資料行填滿模式和其他模式。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的縮放模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 說明如何設定一般用途的調整大小模式。  
  
 [操作說明：以程式設計方式調整儲存格大小以符合 Windows Forms DataGridView 控制項的內容](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 提供示範程式碼，可讓您用來試驗以程式設計方式調整大小。  
  
 [操作說明：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 提供示範程式碼，可讓您用來試驗自動調整大小模式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
## <a name="see-also"></a>請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
