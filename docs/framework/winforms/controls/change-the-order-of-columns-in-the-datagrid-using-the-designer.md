---
title: HOW TO：使用設計工具變更 Windows Forms DataGridView 控制項的資料行順序
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: cb8aeb30e12f7af18b475fd7707fa9d2ede6a299
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939083"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具變更 Windows Forms DataGridView 控制項的資料行順序
當您繫結 Windows Form<xref:System.Windows.Forms.DataGridView>控制項資料來源時，會自動產生的資料行的顯示順序取決於資料來源。 如果此順序是不是您所喜好，您可以變更使用設計工具的資料行的順序。 您也可以將未繫結的資料行新增至控制項，並變更其顯示順序。 如需如何以程式設計方式變更的資料行順序的資訊，請參閱[How to:變更 Windows Form DataGridView 控制項中的資料行的順序](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)  
  
### <a name="to-change-the-column-order-using-the-designer"></a>若要變更使用設計工具的資料行順序  
  
1. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2. 選取的資料行**選取的資料行**清單。  
  
3. 按一下向上箭頭或向下箭號右側**所選資料行**清單，直到所選資料行是在您要的位置。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [如何：新增和移除使用設計工具的 Windows Form DataGridView 控制項中的資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
