---
title: HOW TO：使用設計工具以 Windows Forms ListView 控制項新增和移除項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 6e08a7013242b0dbb433e288c4f8d788cb4e143b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343840"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms ListView 控制項新增和移除項目
加入 Windows Form 中的項目中的程序<xref:System.Windows.Forms.ListView>控制主要包含指定的項目，並將屬性指派給它。 隨時都可以新增或移除清單項目。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>若要新增或移除項目使用設計工具  
  
1. 選取 <xref:System.Windows.Forms.ListView> 控制項。  
  
2. 在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Items%2A>屬性。  
  
     **ListViewItem 集合編輯器**隨即出現。  
  
3. 若要加入的項目，按一下**新增** 按鈕。 您可以再設定屬性的新的項目，例如<xref:System.Windows.Forms.ListView.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。  
  
4. 若要移除的項目，請選取它，然後按一下**移除** 按鈕。  
  
## <a name="see-also"></a>另請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [如何：資料行加入 Windows Form ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：使用 Windows Forms ListView 控制項的資料行顯示子項目](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [如何：Windows Form ListView 控制項中顯示的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [如何：在 Windows Form ListView 控制項中的群組項目](how-to-group-items-in-a-windows-forms-listview-control.md)
