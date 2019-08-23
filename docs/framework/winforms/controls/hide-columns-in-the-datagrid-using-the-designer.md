---
title: 作法：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 35aa1cdeef919d4267cb27da79f183c4c52aefa2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916385"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。 例如, 您可能會想要向具有管理認證的使用者顯示員工薪資資料行, 同時將其隱藏給其他使用者。 或者, 您可能會想要將控制項系結至包含許多資料行的資料來源, 而只是您想要顯示的部分。 在此情況下, 您通常會移除您不想要顯示的資料行, 而不是隱藏它們。 如需詳細資訊，請參閱[如何：使用設計](add-and-remove-columns-in-the-datagrid-using-the-designer.md)工具在 Windows Forms DataGridView 控制項中新增和移除資料行。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-hide-a-column-using-the-designer"></a>若要使用設計工具隱藏資料行

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> , 將`false`屬性設定為。

    > [!NOTE]
    > 藉由清除 [**加入資料行**] 對話方塊中的 [**可見**] 核取方塊, 您也可以在加入資料行時將它隱藏。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
