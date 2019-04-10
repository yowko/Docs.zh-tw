---
title: HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343281"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行
Windows Form<xref:System.Windows.Forms.DataGridView>控制項必須包含資料行，以便顯示資料。 如果您打算以手動方式填入控制項，您必須自行加入資料行。 或者，您可以控制項繫結至資料來源，會產生，並會自動填入資料行。 如果資料來源包含多個資料行，比您想要顯示，您可以移除不必要的資料行。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-a-column-using-the-designer"></a>若要加入資料行使用設計工具  
  
1. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**加入資料行**。  
  
2. 在**加入資料行**對話方塊方塊中，選擇**資料繫結資料行**選項，並選取資料行從資料來源，或選擇**解除繫結的資料行**選項，並定義資料行使用提供的欄位。  
  
3. 按一下 **新增**按鈕以新增資料行，使其出現在設計工具中，如果現有的資料行沒有已填滿控制項顯示區域。  
  
    > [!NOTE]
    >  您可以修改資料行中的屬性**編輯資料行** 對話方塊中，您可以存取從控制項的智慧標籤。  
  
### <a name="to-remove-a-column-using-the-designer"></a>若要移除資料行使用設計工具  
  
1. 選擇**編輯資料行**從控制項的智慧標籤。  
  
2. 選取的資料行**選取的資料行**清單。  
  
3. 按一下 [**移除**] 按鈕來刪除資料行，使其從設計工具中消失。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [HOW TO：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [HOW TO：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
