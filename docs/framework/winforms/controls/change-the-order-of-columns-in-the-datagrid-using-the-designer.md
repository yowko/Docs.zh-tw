---
title: "如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42167c1391ef0820568fa120125bd973f567f0de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序
當您繫結 Windows Form<xref:System.Windows.Forms.DataGridView>控制項至資料來源，會自動產生的資料行的顯示順序取決於資料來源。 如果此順序是不是您所喜好，您可以變更使用設計工具的資料行的順序。 您也可以將未繫結的資料行加入至控制項，並變更其顯示順序。 如需如何以程式設計方式變更的資料行順序的資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的資料行順序](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-change-the-column-order-using-the-designer"></a>若要變更使用設計工具的資料行順序  
  
1.  按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2.  選取的資料行**選取的資料行**清單。  
  
3.  按一下向上或向下箭號右邊的**所選資料行**清單，直到所選資料行是在您要的位置。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
