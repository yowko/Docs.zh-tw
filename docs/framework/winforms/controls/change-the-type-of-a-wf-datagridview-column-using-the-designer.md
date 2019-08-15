---
title: 作法：使用設計工具變更 Windows Forms DataGridView 資料行的類型
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f40ab6fe000f9104b10d5841f52eadf102a91a6b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040473"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>作法：使用設計工具變更 Windows Forms DataGridView 資料行的類型
有時候您會想要變更已經加入至 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項的資料行類型。 例如, 當您將控制項系結至資料來源時, 您可能會想要修改自動產生之部分資料行的類型。 當您顯示的資料表中有資料行包含相關資料表中之資料列的外鍵時, 這會很有用。 在此情況下, 您可能會想要將顯示這些外鍵的文字方塊資料行, 取代為在相關資料表中顯示更有意義之值的下拉式方塊資料行。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>若要使用設計工具變更資料行的類型

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中`ColumnType` , 將屬性設定為新的資料行類型。

    > [!NOTE]
    >  `ColumnType`屬性是僅限設計階段的屬性, 表示代表資料行類型的類別。 它不是在資料行類別中定義的實際屬性。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
