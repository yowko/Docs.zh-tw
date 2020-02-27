---
title: 使用設計工具使 DataGridView 控制項中的資料行成為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 2dd3f8bfcad39ca3d530c79a6e6a8170585f7adf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627951"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀
根據預設，使用者可以修改 Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項中顯示的文字和數值資料。 如果您想要顯示不適用於修改的資料，您必須將包含資料的資料行設為唯讀。 如需如何讓控制項完全唯讀的相關資訊，請參閱[如何：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)。

 下列程式需要具有包含 <xref:System.Windows.Forms.DataGridView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>使用設計工具將資料行設為唯讀

1. 按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**編輯資料行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中，將 [<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>] 屬性設定為 [`true`]。

    > [!NOTE]
    > 您也可以選取 [**加入資料行**] 對話方塊中的 [**唯讀**] 核取方塊，在加入資料行時將它設為唯讀。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [操作說明：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [操作說明：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
