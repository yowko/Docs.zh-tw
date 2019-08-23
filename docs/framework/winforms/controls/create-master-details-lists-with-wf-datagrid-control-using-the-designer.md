---
title: 作法：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 3962b671176ad158b338889140181834e05bbeee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929716"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>作法：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

 如果您<xref:System.Data.DataSet>包含一系列相關的資料表, 您可以使用兩<xref:System.Windows.Forms.DataGrid>個控制項, 以主版詳細資料格式顯示資料。 其中<xref:System.Windows.Forms.DataGrid>一個會被指定為主要方格, 而第二個則指定為詳細資料方格。 當您選取 [主要] 清單中的專案時, [詳細資料] 清單中會顯示所有相關的子專案。 例如, 如果您<xref:System.Data.DataSet>的包含 customers 資料表和相關的 Orders 資料表, 您會將 customers 資料表指定為主要方格, 而 orders 資料表則是詳細資料方格。 從主要方格中選取客戶時, [訂單] 資料表中與該客戶相關聯的所有訂單都會顯示在 [詳細資料] 方格中。

 下列程式需要**Windows 應用程式**專案 ([  > 檔案] [**新增** > **專案** > ] [ **C#視覺效果**] 或 [ **Visual Basic**  > ] **傳統桌面** >  **Windows Forms 應用程式**)。

## <a name="to-create-a-master-details-list-in-the-designer"></a>若要在設計工具中建立主版詳細資料清單

1. 將兩<xref:System.Windows.Forms.DataGrid>個控制項新增至表單。 如需詳細資訊，請參閱[如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。 在 Visual Studio 2005 中, <xref:System.Windows.Forms.DataGrid>控制項預設不會在 [**工具箱**] 中。 如需詳細資訊，請參閱[如何：將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。

    > [!NOTE]
    > 下列步驟不適用於 Visual Studio 2005, 其使用設計階段資料系結的 [**資料來源**] 視窗。 如需詳細資訊, 請參閱[將控制項系結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[如何:在 Windows Forms 應用程式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))中顯示相關資料。

2. 將兩個或多個資料表從**伺服器總管**拖曳至表單。

3. 從 [**資料**] 功能表中, 選取 [**產生資料集**]。

4. 使用 XML 設計工具設定資料表之間的關聯性。 如需詳細資訊, 請參閱 < 如何:在 MSDN 上的 XML 架構和資料集內建立一對多關聯性。

5. 從 [檔案] 功能表中選取 [**全部儲存**], 以儲存關聯性。

6. 設定您想要指定主要方格的控制項,如下所示:<xref:System.Windows.Forms.DataGrid>

    1. <xref:System.Data.DataSet>從<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性的下拉式清單中選取。

    2. 從<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性的下拉式清單中選取主資料表 (例如「Customers」)。

7. 設定您想要指定詳細資料方格的控制項,如下所示:<xref:System.Windows.Forms.DataGrid>

    1. <xref:System.Data.DataSet>從<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性的下拉式清單中選取。

    2. 從<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性的下拉式清單中, 選取 master 和 detail 資料表之間的關聯性 (例如, "Customers. CustOrd")。 若要查看關聯性, 請在下拉式清單中按一下主表旁邊的 **+** 加號 (), 展開節點。

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將 Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
