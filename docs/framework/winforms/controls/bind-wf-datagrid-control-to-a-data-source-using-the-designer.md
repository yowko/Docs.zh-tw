---
title: HOW TO：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源
ms.date: 03/30/2017
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
ms.openlocfilehash: fe54c650e1d19f36d681053c7da47e12527c5827
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320882"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>HOW TO：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form<xref:System.Windows.Forms.DataGrid>控制項專為顯示從資料來源的資訊。 您將控制項繫結在設計階段藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性，或藉由呼叫的執行階段<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。 雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集] 和 [資料檢視。  
  
 如果在設計階段所使用資料來源，比方說，如果表單包含資料集或資料檢視的執行個體，您可以在設計階段方格繫結至資料來源。 然後，您可以預覽資料方格中如下。  
  
 您也可以繫結方格以程式設計的方式，在執行階段。 當您想要設定資料來源，根據您在執行階段取得的資訊時，這非常有用。 例如，應用程式可能會讓使用者指定要檢視之資料表的名稱。 它也是必要的資料來源不在執行階段存在的情況。 這包括資料來源，例如陣列、 集合、 不具類型的資料集，以及資料讀取器。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGrid>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。 在 Visual Studio 2005 裡<xref:System.Windows.Forms.DataGrid>控制項不是處於**工具箱**預設。 如需將它加入資訊，請參閱[How to:將項目加入至工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。 此外在 Visual Studio 2005 中，您可以使用**Zdroje dat**設計階段資料繫結的視窗。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>以資料繫結 DataGrid 控制項至設計工具中的單一資料表  
  
1. 將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至的資料項目物件的屬性。  
  
2. 如果資料來源的資料集，請設定<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性繫結至資料表的名稱。  
  
3. 如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入表單，以填入資料集。  
  
     您使用的確切程式碼取決於資料集從何處取得資料。 如果直接從資料庫填入資料集，您通常會呼叫`Fill`方法的資料配接器，如下列程式碼範例中，會填入資料集所示`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4. （選擇性）將適當的資料表樣式和資料行樣式加入方格中。  
  
     如果不有任何資料表樣式，您會看到資料表，但搭配最少的格式與可見的所有資料行。  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>若要進行資料繫結 DataGrid 控制項中的資料集設計工具中的多個資料表  
  
1. 將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至的資料項目物件的屬性。  
  
2. 如果資料集包含相關的資料表 （也就是如果它包含的關聯性物件），將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為父資料表的名稱。  
  
3. 撰寫程式碼以填入資料集。  
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)
