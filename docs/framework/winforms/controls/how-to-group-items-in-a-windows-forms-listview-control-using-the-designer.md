---
title: 如何：使用設計工具群組 Windows Form ListView 控制項中的項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 40105ba9ffdc6f61cd9a9e382ba5d2610cbcbca2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417304"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具群組 Windows Form ListView 控制項中的項目
分組功能<xref:System.Windows.Forms.ListView>控制項可讓您以群組顯示相關的項目集。 這些群組是在螢幕上分隔包含群組標題的水平群組標頭。 您可以使用<xref:System.Windows.Forms.ListView>群組，使導覽更容易的大型清單依字母順序，分組項目，依日期，或任何其他的邏輯群組。 下圖顯示一些分組的項目。  
  
 ![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。 如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
 若要啟用群組，您必須先建立一或多個<xref:System.Windows.Forms.ListViewGroup>物件在設計工具或以程式設計的方式。 一旦已定義的群組，您可以指派給它的項目。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> 群組是僅適用於[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。 在舊版的作業系統，與群組相關的任何程式碼沒有任何作用，並不會出現群組。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>若要新增或移除群組，在設計工具  
  
1.  在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Groups%2A>屬性。  
  
     **ListViewGroup 集合編輯器**隨即出現。  
  
2.  若要新增的群組，請按一下**新增** 按鈕。 您可以再設定屬性的新群組，例如<xref:System.Windows.Forms.ListViewGroup.Header%2A>和<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>屬性。 若要移除群組，請選取它，然後按一下**移除** 按鈕。  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>若要將項目指派給設計工具中的群組  
  
1.  在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Items%2A>屬性。  
  
     **ListViewItem 集合編輯器**隨即出現。  
  
2.  若要加入新項目，按一下**新增** 按鈕。 您可以再設定屬性的新的項目，例如<xref:System.Windows.Forms.ListViewItem.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。  
  
3.  選取<xref:System.Windows.Forms.ListViewItem.Group%2A>屬性，然後從下拉式清單中選擇 群組。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP 功能和 Windows Forms 控制項](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
