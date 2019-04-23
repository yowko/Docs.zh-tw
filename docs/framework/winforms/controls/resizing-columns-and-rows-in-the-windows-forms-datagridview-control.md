---
title: 調整 Windows Form DataGridView 控制項中資料行和資料列的大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e1fa2d57cfb2cd374d691fe03a0e0bdbd3ad7141
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138108"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>調整 Windows Form DataGridView 控制項中資料行和資料列的大小
`DataGridView`控制項提供許多選項可以自訂其資料行和資料列的調整大小行為。 一般而言，`DataGridView`不調整大小的資料格根據其內容。 相反地，它們會裁剪掉任何大於資料格的顯示值。 如果內容可以顯示為字串，則資料格會顯示它在工具提示。  
  
 根據預設，使用者可以拖曳資料列、 資料行和標頭分隔線，使用滑鼠，以顯示詳細資訊。 使用者也可以按兩下分割線，以自動調整大小相關聯的資料列、 資料行或標頭群組列根據其內容。  
  
 `DataGridView`控制項提供屬性、 方法和事件可讓您自訂或停用所有這些使用者導向的行為。 此外，您也可以以程式設計方式調整資料列、 資料行和標頭，以適合其內容，或者您可以將其設定為每當內容變更時自動調整本身大小。 您也可以設定自動將您指定的比例控制項可用寬度的資料行。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)  
 描述的選項，調整資料列、 資料行和標頭。 也提供調整大小相關的屬性和方法的詳細資訊，並描述常見使用案例。  
  
 [Windows Forms DataGridView 控制項中的資料行填入模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 描述資料行填入模式的詳細資訊，並提供示範程式碼，可供您試驗資料行填入模式與其他模式。  
  
 [如何：設定 Windows Forms DataGridView 控制項的縮放模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 描述如何設定一般用途的縮放模式。  
  
 [如何：以程式設計方式調整大小以符合內容，在 Windows Form DataGridView 控制項中的資料格](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 提供示範程式碼，可供您試驗以程式設計方式調整大小。  
  
 [如何：自動調整大小的資料格，當 Windows Form DataGridView 控制項中的內容變更](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 提供示範程式碼，可供您試驗自動調整大小模式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
