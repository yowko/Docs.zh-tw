---
title: 使用設計工具建立具有 DataGrid 控制項的主版詳細資料清單
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743393"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>如何：使用設計工具搭配 Windows Form DataGrid 控制項建立主版詳細資料清單

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

 如果您的 <xref:System.Data.DataSet> 包含一系列相關的資料表，您可以使用兩個 <xref:System.Windows.Forms.DataGrid> 控制項，以主版詳細資料格式顯示資料。 其中一個 <xref:System.Windows.Forms.DataGrid> 會指定為主要方格，而第二個則指定為詳細資料方格。 當您選取 [主要] 清單中的專案時，[詳細資料] 清單中會顯示所有相關的子專案。 例如，如果您的 <xref:System.Data.DataSet> 包含 Customers 資料表和相關的 Orders 資料表，您會將 Customers 資料表指定為主要方格，而 Orders 資料表則為詳細資料方格。 從主要方格中選取客戶時，[訂單] 資料表中與該客戶相關聯的所有訂單都會顯示在 [詳細資料] 方格中。

 下列程式需要**Windows 應用程式**專案（**File** > **New** > **project** > **Visual C#** 或**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**）。

## <a name="to-create-a-master-details-list-in-the-designer"></a>若要在設計工具中建立主版詳細資料清單

1. 將兩個 <xref:System.Windows.Forms.DataGrid> 控制項新增至表單。 如需詳細資訊，請參閱[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。 在 Visual Studio 2005 中，預設不會在 [**工具箱**] 中使用 <xref:System.Windows.Forms.DataGrid> 控制項。 如需詳細資訊，請參閱[如何：將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。

    > [!NOTE]
    > 下列步驟不適用於 Visual Studio 2005，其使用設計階段資料系結的 [**資料來源**] 視窗。 如需詳細資訊，請參閱將控制項系結[至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[如何：在 Windows Forms 應用程式中顯示相關資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))。

2. 將兩個或多個資料表從**伺服器總管**拖曳至表單。

3. 從 [**資料**] 功能表中，選取 [**產生資料集**]。

4. 使用 XML 設計工具設定資料表之間的關聯性。 如需詳細資訊，請參閱 MSDN 上的「如何：在 XML 架構和資料集中建立一對多關聯性」。

5. 從 [檔案] 功能表中選取 [**全部儲存** **]，以**儲存關聯性。

6. 設定您想要指定主要方格的 <xref:System.Windows.Forms.DataGrid> 控制項，如下所示：

    1. 從 [<xref:System.Windows.Forms.DataGrid.DataSource%2A>] 屬性的下拉式清單中選取 [<xref:System.Data.DataSet>]。

    2. 從 [<xref:System.Windows.Forms.DataGrid.DataMember%2A>] 屬性的下拉式清單中，選取主資料表（例如「Customers」）。

7. 設定您想要指定詳細資料方格的 <xref:System.Windows.Forms.DataGrid> 控制項，如下所示：

    1. 從 [<xref:System.Windows.Forms.DataGrid.DataSource%2A>] 屬性的下拉式清單中選取 [<xref:System.Data.DataSet>]。

    2. 從 [<xref:System.Windows.Forms.DataGrid.DataMember%2A>] 屬性的下拉式清單中，選取 master 和 detail 資料表之間的關聯性（例如，"Customers. CustOrd"）。 若要查看關聯性，請在下拉式清單中按一下主表旁邊的加號（ **+** ），展開節點。

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將 Windows Forms DataGrid 控制項繫結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
