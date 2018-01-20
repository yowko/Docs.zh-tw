---
title: "如何：使用設計工具搭配 Windows Form DataGrid 控制項建立主版詳細資料清單"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1526a6e54078ea3dc0500c39a8fc2feda44d901
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>如何：使用設計工具搭配 Windows Form DataGrid 控制項建立主版詳細資料清單
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您<xref:System.Data.DataSet>包含一系列相關的資料表，您可以使用兩個<xref:System.Windows.Forms.DataGrid>控制項以顯示在主版詳細資料格式的資料。 一個<xref:System.Windows.Forms.DataGrid>指定為主要方格中，與第二個指定為詳細資料方格。 當您的主機清單中選取一個項目時，所有相關的子系項目會顯示在詳細資料清單。 例如，如果您<xref:System.Data.DataSet>包含 Customers 資料表和相關的 Orders 資料表，您會指定為主要的方格的 [客戶] 資料表和訂單資料表詳細資料方格。 從主版方格選取客戶時，所有相關 [Orders] 資料表中與該客戶的訂單會顯示詳細資料方格中。  
  
 下列程序需要**Windows 應用程式**專案。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>在設計工具中建立主從式清單  
  
1.  加入兩個<xref:System.Windows.Forms.DataGrid>控制項加入表單。 如需詳細資訊，請參閱[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。 在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**預設。 如需詳細資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
    > [!NOTE]
    >  下列步驟不適用於[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，它會使用**資料來源**設計階段資料繫結的視窗。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[How to： 在 Windows Forms 應用程式中顯示相關資料](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)。  
  
2.  將兩個或多個資料表，從**伺服器總管**至表單。  
  
3.  從**資料**功能表上，選取**產生資料集**。  
  
4.  設定使用 XML 設計工具的資料表之間的關聯性。 如需詳細資訊，請參閱 「 如何： 建立一對多關聯性中的 XML 結構描述和資料集"MSDN 上。  
  
5.  儲存選取的關聯性**全部儲存**從**檔案**功能表。  
  
6.  設定<xref:System.Windows.Forms.DataGrid>控制項，您想要指定主要格線，如下所示：  
  
    1.  選取<xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。  
  
    2.  從下拉式清單中選取主要資料表 （例如，「 客戶 」）<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。  
  
7.  設定<xref:System.Windows.Forms.DataGrid>控制您想要將詳細資料方格中，指定，如下所示：  
  
    1.  選取<xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。  
  
    2.  選取從下拉式清單中的主要和詳細資料表之間的關聯性 (例如，"Customers.CustOrd 」)<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 若要查看的關聯性，請展開節點加上的 (**+**) 旁邊的下拉式清單中主要資料表。  
  
## <a name="see-also"></a>請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [操作說明：將 Windows Forms DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
