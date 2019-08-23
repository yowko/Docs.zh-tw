---
title: 作法：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 7a3029192ab0da4a954dfd7d3d258a00b154924e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957118"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行
Windows Forms <xref:System.Windows.Forms.DataGridView>控制項必須包含資料行, 才能顯示資料。 如果您打算手動填入控制項, 就必須自行加入資料行。 或者, 您可以將控制項系結至資料來源, 以自動產生和填入資料行。 如果資料來源包含比您想要顯示的更多欄, 您可以移除不必要的資料行。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-add-a-column-using-the-designer"></a>若要使用設計工具加入資料行

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [加入資料**行**]。

2. 在 [**加入資料行**] 對話方塊中, 選擇 [資料系結資料**行**] 選項, 並從資料來源選取資料行, 或選擇 [未系結資料**行**] 選項, 並使用所提供的欄位來定義資料行。

3. 按一下 [**新增**] 按鈕以加入資料行, 如果現有的資料行尚未填滿控制項顯示區域, 則會使其出現在設計工具中。

    > [!NOTE]
    > 您可以在 [**編輯資料行**] 對話方塊中修改資料行屬性, 您可以從控制項的智慧標籤進行存取。

## <a name="to-remove-a-column-using-the-designer"></a>若要使用設計工具來移除資料行

1. 從控制項的智慧標籤中選擇 [**編輯資料行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 按一下 [**移除**] 按鈕以刪除資料行, 使其從設計工具中消失。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
