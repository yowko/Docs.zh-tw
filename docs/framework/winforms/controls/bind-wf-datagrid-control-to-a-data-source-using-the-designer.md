---
title: 作法：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源
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
ms.openlocfilehash: de8b8d16f45221fbafe9f61ca634f144d8f6f6ae
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040004"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>作法：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源

> [!NOTE]
>            <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

 Windows Forms <xref:System.Windows.Forms.DataGrid>控制項是特別設計來顯示資料來源中的資訊。 在設計階段, 您可以藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性, 或在<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>執行時間呼叫方法來系結控制項。 雖然您可以顯示來自各種資料來源的資料, 但最常見的來源是資料集和資料檢視。

 如果資料來源在設計階段可用 (例如, 如果表單包含資料集或資料檢視的實例), 您可以在設計階段將方格系結至資料來源。 接著, 您可以在方格中預覽資料的樣子。

 您也可以在執行時間以程式設計方式系結方格。 當您想要根據您在執行時間取得的資訊來設定資料來源時, 這會很有用。 例如, 應用程式可能會讓使用者指定要查看的資料表名稱。 在設計階段, 資料來源不存在的情況下也是必要的。 這包括資料來源, 例如陣列、集合、不具類型的資料集和資料讀取器。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGrid>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。 在 Visual Studio 2005 中, <xref:System.Windows.Forms.DataGrid>控制項預設不會在 [**工具箱**] 中。 如需新增它的相關資訊[, 請參閱如何:將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。 此外, 在 Visual Studio 2005 中, 您可以使用 [**資料來源**] 視窗進行設計階段資料系結。 如需詳細資訊, 請參閱[將控制項系結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>若要將 DataGrid 控制項資料系結至設計工具中的單一資料表

1. 將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性設定為包含您要系結之資料項目的物件。

2. 如果資料來源是資料集, 請將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設定為要系結之資料表的名稱。

3. 如果資料來源是資料集或根據資料集資料表的資料檢視, 請將程式碼加入至表單, 以填滿資料集。

     您所使用的確切程式碼取決於資料集取得資料的位置。 如果直接從資料庫填入資料集, 您通常會呼叫`Fill`資料介面卡的方法, 如下列程式碼範例所示, 它會填入名`DsCategories1`為的資料集:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. 選擇性在方格中加入適當的資料表樣式和資料行樣式。

     如果沒有資料表樣式, 您會看到資料表, 但最小的格式和所有資料行都是可見的。

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>若要將 DataGrid 控制項資料系結至設計工具中資料集內的多個資料表

1. 將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性設定為包含您要系結之資料項目的物件。

2. 如果資料集包含相關的資料表 (亦即, 如果它包含關聯性物件), 請<xref:System.Windows.Forms.DataGrid.DataMember%2A>將屬性設定為父資料表的名稱。

3. 撰寫程式碼以填滿資料集。

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將資料表和資料行加入至 Windows Forms DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)
