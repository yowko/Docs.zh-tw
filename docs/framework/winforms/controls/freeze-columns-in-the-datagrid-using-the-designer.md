---
title: HOW TO：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 397a2c5a7879be8c1bef7e04e72cf675f25d0fb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344308"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。 比方說，當您顯示客戶資訊，其中包含許多資料行的資料表時，它可用於您隨時都能在其他資料行的可見區域外捲動時顯示客戶的名稱。  
  
 若要達到這種行為，您可以凍結控制項中的資料行。 當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。 凍結的資料行會留在原處，而其他所有資料行則可以捲動。 如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。 使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-freeze-a-column-using-the-designer"></a>若要凍結資料行使用設計工具  
  
1. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2. 選取的資料行**選取的資料行**清單。  
  
3. 在 **資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>屬性設`true`。  
  
    > [!NOTE]
    >  您也可以將它加入選取時凍結資料行**Frozen**方塊中**加入資料行** 對話方塊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [如何：新增和移除使用設計工具的 Windows Form DataGridView 控制項中的資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：啟用 Windows Form DataGridView 控制項中使用設計工具中的資料行重新調整順序](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [如何：顯示全球化 Windows Form 中由右至左的文字](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
