---
title: 作法：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: d38c8d73bc70e7e521b476ca78c8f102d003c538
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040328"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。 例如, 當您顯示包含許多資料行的客戶資訊資料表時, 您可以隨時顯示客戶名稱, 同時讓其他資料行在可見區域之外滾動。

 若要達到這種行為，您可以凍結控制項中的資料行。 當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。 凍結的資料行會留在原處，而其他所有資料行則可以捲動。 如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。 使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-freeze-a-column-using-the-designer"></a>若要使用設計工具凍結資料行

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> , 將`true`屬性設定為。

    > [!NOTE]
    >  您也可以選取 [**加入資料行**] 對話方塊中的 [**凍結**] 方塊來加入資料行。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新排列](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [如何：在全球化的 Windows Forms 中顯示由右至左的文字](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
