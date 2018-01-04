---
title: "如何：使用設計工具在 Windows Form DataGrid 控制項中加入表格和資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48471427baccfa9fb8e7c3aedbb9576ab0d34243
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>如何：使用設計工具在 Windows Form DataGrid 控制項中加入表格和資料行
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以在 Windows Form 顯示資料<xref:System.Windows.Forms.DataGrid>中資料表和資料行，藉由建立控制項<xref:System.Windows.Forms.DataGridTableStyle>物件並將它們加入至<xref:System.Windows.Forms.GridTableStylesCollection>物件，它透過存取<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。 每個資料表樣式顯示的任何資料表中所指定內容<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性<xref:System.Windows.Forms.DataGridTableStyle>。 根據預設，沒有指定的資料行樣式的資料表樣式會顯示資料的資料表中的所有資料行。 您可以限制資料表的哪些資料行出現加<xref:System.Windows.Forms.DataGridColumnStyle>物件加入至<xref:System.Windows.Forms.GridColumnStylesCollection>，這透過存取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>每個屬性<xref:System.Windows.Forms.DataGridTableStyle>。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGrid>控制項。 如需如何設定這類專案的資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。 根據預設，在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**。 如需將它加入資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>若要將資料表加入至設計工具中的 DataGrid 控制項  
  
1.  若要顯示資料表中的資料，您必須先繫結<xref:System.Windows.Forms.DataGrid>控制項至資料集。 如需詳細資訊，請參閱[How to： 將 Windows Form DataGrid 控制項繫結至資料來源使用設計工具](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)。  
  
2.  選取<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性中 [屬性] 視窗中，然後按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊若要顯示屬性**DataGridTableStyle 集合編輯器**。  
  
3.  在 集合編輯器中，按一下 **新增**插入資料表樣式。  
  
4.  按一下**確定**關閉集合編輯器，，然後重新開啟它，依序按一下省略符號按鈕旁的 <xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。  
  
     當您重新開啟集合編輯器 時，繫結控制項至任何資料的資料表會出現在下拉式清單<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>資料表樣式的屬性。  
  
5.  在**成員**方塊的集合編輯器中，按一下資料表樣式。  
  
6.  在**屬性**集合編輯器中，選取方塊<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>您想要顯示的資料表的值。  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>若要將資料行加入至設計工具中的 DataGrid 控制項  
  
1.  在**成員**方塊**DataGridTableStyle 集合編輯器**，選取適當的資料表樣式。 在**屬性**集合編輯器中，選取方塊<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>集合，然後按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 以顯示在內容旁**DataGridColumnStyle 集合編輯器**。  
  
2.  在 集合編輯器中，按一下 **新增**插入資料行樣式，或按一下向下箭號旁**新增**來指定資料行類型。  
  
     在下拉式清單方塊中，您可以選取<xref:System.Windows.Forms.DataGridTextBoxColumn>或<xref:System.Windows.Forms.DataGridBoolColumn>型別。  
  
3.  按一下 確定 關閉**DataGridColumnStyle 集合編輯器**，然後重新開啟它，依序按一下省略符號按鈕旁的 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性。  
  
     當您重新開啟集合編輯器 時，資料表中的繫結的資料的任何資料行就會出現在下拉式清單<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>屬性的資料行樣式。  
  
4.  在**成員**方塊的集合編輯器中，按一下 資料行樣式。  
  
5.  在**屬性**集合編輯器中，選取方塊<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>您想要顯示的資料行的值。  
  
## <a name="see-also"></a>請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
