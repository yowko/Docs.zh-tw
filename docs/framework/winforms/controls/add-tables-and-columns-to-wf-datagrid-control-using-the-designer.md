---
title: 作法：使用設計工具將資料表和資料行新增至 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: a5955840988cb747b21f32efbd5c6091a86f483a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959525"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>HOW TO：使用設計工具將資料表和資料行新增至 Windows Forms DataGrid 控制項

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

您可以在 Windows Form 中顯示資料<xref:System.Windows.Forms.DataGrid>中資料表和資料行，藉由建立控制項<xref:System.Windows.Forms.DataGridTableStyle>物件，並將它們加入至<xref:System.Windows.Forms.GridTableStylesCollection>物件，這透過存取<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。 每個資料表樣式會顯示任何資料表中指定的內容<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性<xref:System.Windows.Forms.DataGridTableStyle>。 根據預設，沒有指定的資料行樣式的資料表樣式會顯示資料的資料表內的所有資料行。 您可以限制哪些資料行從資料表顯示加上<xref:System.Windows.Forms.DataGridColumnStyle>物件至<xref:System.Windows.Forms.GridColumnStylesCollection>，這透過存取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>每個屬性<xref:System.Windows.Forms.DataGridTableStyle>。

下列程序需要**Windows 應用程式**專案，其表單包含<xref:System.Windows.Forms.DataGrid>控制項。 如需有關如何設定這類專案的資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。 根據預設，在 Visual Studio 2005<xref:System.Windows.Forms.DataGrid>控制項不是處於**工具箱**。 如需將它加入資訊，請參閱[How to:將項目加入至工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>若要將資料表加入至設計工具中的 DataGrid 控制項

1. 若要顯示資料表中的資料，您必須先繫結<xref:System.Windows.Forms.DataGrid>資料集的控制項。 如需詳細資訊，請參閱[如何：將 Windows Forms DataGrid 控制項繫結至資料來源，使用設計工具](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)。

2. 選取 <xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>[屬性] 視窗中的屬性，然後按一下省略符號按鈕 (![的 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁邊要顯示的屬性**Styl 集合編輯器**。

3. 在集合編輯器 中，按一下**新增**插入資料表樣式。

4. 按一下 [ **[確定]** 以關閉集合編輯器] 中，並再重新開啟它，依序按一下省略符號按鈕旁<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。

     當您重新開啟集合編輯器時，任何繫結至控制項的資料表會出現在下拉式清單，如<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>資料表樣式的屬性。

5. 在 [**成員**] 方塊中的集合編輯器] 中，按一下 [資料表樣式。

6. 在 **屬性** 方塊中的 集合編輯器中，選取<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>您想要顯示的資料表的值。

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>若要將資料行加入至設計工具中的 DataGrid 控制項

1. 在 **成員**的方塊**Styl 集合編輯器**，選取適當的資料表樣式。 在**屬性**] 方塊中的 [集合編輯器中，選取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>集合，然後按一下省略符號按鈕 (![的 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁要顯示的屬性**DataGridColumnStyle 集合編輯器**。

2. 在集合編輯器 中，按一下**新增**插入資料行樣式，或按一下向下箭號旁**新增**來指定資料行類型。

     在下拉式清單方塊中，您可以選取<xref:System.Windows.Forms.DataGridTextBoxColumn>或<xref:System.Windows.Forms.DataGridBoolColumn>型別。

3. 按一下 [確定] 以關閉**DataGridColumnStyle 集合編輯器**，然後重新開啟它，依序按一下省略符號按鈕旁<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性。

     當您重新開啟集合編輯器時，任何資料行，資料表中的繫結的資料會出現在下拉式清單，如<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>屬性的資料行樣式。

4. 在 [**成員**] 方塊中的集合編輯器] 中，按一下 [資料行樣式。

5. 在 **屬性** 方塊中的 集合編輯器中，選取<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>您想要顯示的資料行的值。

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
