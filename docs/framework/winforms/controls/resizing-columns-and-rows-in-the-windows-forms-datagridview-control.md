---
title: "調整 Windows Form DataGridView 控制項中資料行和資料列的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3621b05f1faae671d93106f50dfef1311959e48e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>調整 Windows Form DataGridView 控制項中資料行和資料列的大小
`DataGridView`控制項提供許多自訂其資料行和資料列的調整大小行為的選項。 一般而言，`DataGridView`不調整大小的資料格根據其內容。 相反地，它們會裁剪任何大於儲存格的顯示值。 如果內容可以顯示為字串，則資料格會顯示其工具提示中。  
  
 根據預設，使用者可以拖曳資料列、 資料行和滑鼠來顯示詳細資訊的行首分割線。 使用者也可以按兩下分割線，自動調整大小的相關資料列、 資料行或標頭寬線根據其內容。  
  
 `DataGridView`控制項提供屬性、 方法和事件，可讓您自訂或停用所有這些使用者導向的行為。 此外，您也可以透過程式設計方式調整資料列、 資料行和標頭，以適合其內容，或者您可以將其設定為每當內容變更時自動調整本身大小。 您也可以設定自動分割中您所指定的比例控制項可用寬度的資料行。  
  
## <a name="in-this-section"></a>本章節內容  
 [Windows Forms DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 描述調整資料列、 資料行和標頭的選項。 也提供調整大小相關的屬性和方法的詳細資訊，並說明常見使用案例。  
  
 [Windows Forms DataGridView 控制項中的資料行填入模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 描述資料行填入模式中的詳細資料，並提供示範程式碼，可讓您試驗資料行填入模式與其他模式。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的縮放模式](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 描述如何設定一般用途的調整大小模式。  
  
 [操作說明：以程式設計方式調整儲存格大小以符合 Windows Forms DataGridView 控制項的內容](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 提供示範程式碼，可讓您試驗以程式設計方式調整大小。  
  
 [操作說明：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 提供示範程式碼，可讓您試驗自動調整大小模式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
## <a name="see-also"></a>另請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
