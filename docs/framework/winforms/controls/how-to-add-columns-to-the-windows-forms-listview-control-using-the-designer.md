---
title: 如何：使用設計工具在 Windows Form ListView 控制項中加入資料行
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 4c696644e61004bcac48399ffc752e40675642fc
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027826"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具在 Windows Form ListView 控制項中加入資料行
Windows Forms<xref:System.Windows.Forms.ListView>控制項可以顯示多個資料行，每個清單項目中的時機**詳細資料**檢視。 您可以使用資料行來顯示數種類型的每個清單項目的相關資訊。 例如，檔案名稱、 檔案類型、 大小和檔案上次修改的日期，可以顯示一份檔案。 如需有關擴展的資料行，建立之後，請參閱[如何： 使用 Windows Forms ListView 控制項的資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。 如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-columns-in-the-designer"></a>若要加入至設計工具的資料行  
  
1.  在 [**屬性**] 視窗中，將控制項的<xref:System.Windows.Forms.ListView.View%2A>屬性設<xref:System.Windows.Forms.View.Details>。  
  
2.  在 [**屬性**] 視窗中，按一下**省略符號** 按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.ListView.Columns%2A>屬性。  
  
     **ColumnHeader 集合編輯器**隨即出現。  
  
3.  使用**新增**按鈕以新增新的資料行。 然後，您可以選取資料行標頭，並設定其文字 （資料行的標題）、 文字對齊方式，與寬度。  
  
## <a name="see-also"></a>另請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [操作說明：顯示 Windows Forms ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
