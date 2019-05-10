---
title: HOW TO：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 46825eeb2befab7f11a87451da53a773a6ce2ad2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648219"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您<xref:System.Data.DataSet>包含一系列相關的資料表，您可以使用兩個<xref:System.Windows.Forms.DataGrid>主版詳細資料的格式顯示資料的控制項。 一個<xref:System.Windows.Forms.DataGrid>指定為主要方格中，與第二個指定為詳細資料方格。 當您選取的主機清單中的項目時，所有相關的子系項目會顯示在詳細資料清單。 比方說，如果您<xref:System.Data.DataSet>包含 Customers 資料表和相關的 Orders 資料表中，您會指定為主要格線的 [客戶] 資料表和 Orders 資料表詳細資料方格。 主要方格中選取客戶時，詳細資料方格中就會顯示所有相關聯的 Orders 資料表中與該客戶的訂單。  
  
 下列程序需要**Windows 應用程式**專案 (**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>若要在設計工具中建立主版詳細資料清單  
  
1. 新增兩個<xref:System.Windows.Forms.DataGrid>控制項加入表單。 如需詳細資訊，請參閱[如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。 在 Visual Studio 2005 裡<xref:System.Windows.Forms.DataGrid>控制項不是處於**工具箱**預設。 如需詳細資訊，請參閱[如何：將項目加入至工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。  
  
    > [!NOTE]
    >  下列步驟並不適用於 Visual Studio 2005，它會使用**Zdroje dat**設計階段資料繫結的視窗。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[How to:資料在 Windows Forms 應用程式中顯示相關](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))。  
  
2. 將兩個或多個資料表，從**伺服器總管**至表單。  
  
3. 從**資料**功能表上，選取**產生的資料集**。  
  
4. 設定使用 XML 設計工具的資料表之間的關聯性。 如需詳細資訊，請參閱 「 如何：建立 XML 結構描述與資料集中的一對多關聯性"MSDN 上。  
  
5. 儲存選取的關聯性**全部儲存**從**檔案**功能表。  
  
6. 設定<xref:System.Windows.Forms.DataGrid>控制您想要指定主版方格中，如下所示：  
  
    1. 選取 <xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。  
  
    2. 從下拉式清單中選取主要資料表中 （例如，「 客戶 」）<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。  
  
7. 設定<xref:System.Windows.Forms.DataGrid>控制您想要指定詳細資料方格中，如下所示：  
  
    1. 選取 <xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。  
  
    2. 選取 master] 和 [詳細資料的資料表，從下拉式清單中之間的關聯性 (例如，"Customers.CustOrd 」)<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 若要查看的關聯性，請按一下加號展開的節點 (**+**) 旁邊下拉式清單中的主資料表。  
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將 Windows Forms DataGrid 控制項繫結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
