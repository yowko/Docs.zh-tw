---
title: 使用設計工具隱藏 DataGridView 控制項中的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738650"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具隱藏 Windows Form DataGridView 控制項中的資料行
有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。 例如，您可能會想要向具有管理認證的使用者顯示員工薪資資料行，同時將其隱藏給其他使用者。 或者，您可能會想要將控制項系結至包含許多資料行的資料來源，而只是您想要顯示的部分。 在此情況下，您通常會移除您不想要顯示的資料行，而不是隱藏它們。 如需詳細資訊，請參閱[如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)。

 下列程式需要具有包含 <xref:System.Windows.Forms.DataGridView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

## <a name="to-hide-a-column-using-the-designer"></a>若要使用設計工具隱藏資料行

1. 按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像（![智慧標籤](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")圖像），然後選取 [**編輯資料行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中，將 [<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>] 屬性設定為 [`false`]。

    > [!NOTE]
    > 藉由清除 [**加入資料行**] 對話方塊中的 [**可見**] 核取方塊，您也可以在加入資料行時將它隱藏。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [操作說明：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
