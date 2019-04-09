---
title: HOW TO：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 8639c1e6f4382c1f91ed2c777b1b0ff29c5a60a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113512"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀
根據預設，使用者可以修改文字和數值的資料顯示在 Windows Form<xref:System.Windows.Forms.DataGridView>控制項。 如果您想要顯示不是用於修改的資料，您必須進行的資料行包含唯讀的資料。 如需如何將控制項設完全唯讀的資訊，請參閱[How to:防止資料列中新增和刪除 Windows Form DataGridView 控制項使用設計工具](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>若要將資料行設為唯讀模式使用設計工具  
  
1.  按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2.  選取的資料行**選取的資料行**清單。  
  
3.  在 **資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>屬性設`true`。  
  
    > [!NOTE]
    >  您也可以進行資料行唯讀狀態時將它加入選取**Read Only**中的核取方塊**加入資料行** 對話方塊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [HOW TO：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [HOW TO：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [HOW TO：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
