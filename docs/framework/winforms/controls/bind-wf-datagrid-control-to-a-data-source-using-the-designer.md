---
title: "如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3913ffe046bb55e31d8be223061af61371a47418
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form<xref:System.Windows.Forms.DataGrid>控制項特別設計來顯示資料來源的資訊。 您將控制項繫結在設計階段藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性，或藉由呼叫的執行階段<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。 雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集和資料的檢視。  
  
 如果在執行階段可使用資料來源 — 比方說，如果表單包含多個資料集或資料檢視的執行個體，您可以在設計階段格線繫結至資料來源。 然後，您可以預覽資料方格中的外觀為何。  
  
 您也可以在執行階段以程式設計的方式，結合方格。 當您想要設定資料來源，根據您在執行階段取得的資訊，這非常有用。 例如，應用程式可能會讓使用者指定要檢視之資料表的名稱。 它也是必要的資料來源不在執行階段存在。 這包括資料來源，例如陣列、 集合、 不具類型資料集，以及資料讀取器。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGrid>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。 在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**預設。 如需將它加入資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)。 此外在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，您可以使用**資料來源**設計階段資料繫結的視窗。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>若要進行資料繫結 DataGrid 控制項設計工具中的單一資料表  
  
1.  將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至資料項目物件的屬性。  
  
2.  如果資料來源的資料集，請設定<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為要繫結至資料表的名稱。  
  
3.  如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入至表單，以填入資料集。  
  
     您使用的實際程式碼會取決於資料集從何處取得資料。 如果直接從資料庫填入資料集，您通常會呼叫`Fill`資料配接器，如下列程式碼範例，會填入資料集呼叫的方法`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  （選擇性）將適當的資料表樣式和資料行樣式加入至方格中。  
  
     如果有任何資料表樣式，您會看到資料表，但最少的格式和可見的所有資料行。  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>若要進行資料繫結 DataGrid 控制項中的資料集設計工具中的多個資料表  
  
1.  將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至資料項目物件的屬性。  
  
2.  如果資料集包含相關的資料表 （亦即，如果它包含關聯物件），將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為父資料表的名稱。  
  
3.  撰寫程式碼以填入資料集。  
  
## <a name="see-also"></a>請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)
