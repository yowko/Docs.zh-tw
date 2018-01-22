---
title: "如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdd208d589c6b38088074f6d94045651df7049e8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式
表格式資料通常會以類似 ledger 的格式，交替資料列中有不同的背景色彩。 這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。  
  
 利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。 您可以使用例如前景色彩和字型、 背景色彩以外的樣式特性，來區分替代資料列。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="define-styles-for-alternating-rows"></a>為替代資料列定義的樣式  
  
1.  選取<xref:System.Windows.Forms.DataGridView>設計工具中的控制項。  
  
2.  在**屬性**視窗中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>屬性。  
  
3.  在**CellStyle 產生器**對話方塊中，藉由設定屬性，定義的樣式，並使用**預覽**窗格，即可確認您的選擇。 您指定的樣式會用於顯示在控制項中，第二個啟動的其他每個資料列。  
  
4.  若要定義剩餘的資料列的樣式，請重複步驟 2 和 3 使用<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性。  
  
    > [!NOTE]
    >  使用繼承自多個屬性的樣式來顯示資料格。 如需樣式繼承的詳細資訊，請參閱[Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [使用設計工具搭配 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
