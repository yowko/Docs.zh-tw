---
title: 作法：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039813"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀
根據預設, 使用者可以修改顯示在 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項中的文字和數值資料。 如果您想要顯示不適用於修改的資料, 您必須將包含資料的資料行設為唯讀。 如需如何讓控制項完全唯讀的相關資訊, 請參閱[如何:使用設計](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>使用設計工具將資料行設為唯讀

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> , 將`true`屬性設定為。

    > [!NOTE]
    >  您也可以選取 [**加入資料行**] 對話方塊中的 [**唯讀**] 核取方塊, 在加入資料行時將它設為唯讀。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
