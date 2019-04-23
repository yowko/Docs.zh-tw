---
title: HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: aa81eb7470b818fa2b65200503e5ce65b467c0f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324444"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。 例如，您可能想要顯示員工薪資資料行具有管理認證，同時隱藏其他使用者的使用者。 或者，您可能要將控制項繫結至資料來源，其中包含您想要顯示的只有其中一些的許多資料行。 在此情況下，您通常會移除您不想要顯示，而不是隱藏它們的資料行。 如需詳細資訊，請參閱[如何：新增和移除資料行中的 Windows Form DataGridView 控制項使用設計工具](add-and-remove-columns-in-the-datagrid-using-the-designer.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-hide-a-column-using-the-designer"></a>若要隱藏資料行使用設計工具  
  
1. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2. 選取的資料行**選取的資料行**清單。  
  
3. 在 **資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>屬性設`false`。  
  
    > [!NOTE]
    >  您也可以新增藉由清除時隱藏資料行**Visible**中的核取方塊**加入資料行** 對話方塊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [如何：新增和移除使用設計工具的 Windows Form DataGridView 控制項中的資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
