---
title: "如何：使用設計工具群組 Windows Form ListView 控制項中的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c9dc3a12227d3c9bfd64c97be61e69b50d2bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具群組 Windows Form ListView 控制項中的項目
分組功能<xref:System.Windows.Forms.ListView>控制項可讓您以顯示群組中的項目相關的設定。 這些群組是在螢幕上分隔包含群組標題的水平群組標頭。 您可以使用<xref:System.Windows.Forms.ListView>群組，使導覽更容易的大型清單分組為項目依字母順序，依日期，或任何其他邏輯群組。 下圖顯示一些群組項目。  
  
 ![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.ListView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
 若要啟用群組，您必須先建立一或多個<xref:System.Windows.Forms.ListViewGroup>物件在設計工具或以程式設計的方式。 一旦已定義群組，您可以指定項目。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView>群組是僅適用於[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。 在舊版作業系統，與群組相關的任何程式碼都無效，不會出現群組。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>若要加入或移除群組，在設計工具  
  
1.  在**屬性**視窗中，按一下**省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Groups%2A>屬性。  
  
     **ListViewGroup 集合編輯器**隨即出現。  
  
2.  若要加入群組，按一下**新增** 按鈕。 您可以再設定屬性的新群組，例如<xref:System.Windows.Forms.ListViewGroup.Header%2A>和<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>屬性。 若要移除群組，請選取它，然後按一下**移除** 按鈕。  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>若要將項目指派給設計工具中的群組  
  
1.  在**屬性**視窗中，按一下**省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Items%2A>屬性。  
  
     **ListViewItem 集合編輯器**隨即出現。  
  
2.  若要加入新項目，按一下**新增** 按鈕。 您可以再設定屬性的新項目，例如<xref:System.Windows.Forms.ListViewItem.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。  
  
3.  選取<xref:System.Windows.Forms.ListViewItem.Group%2A>屬性，並從下拉式清單中選擇群組。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP 功能和 Windows Forms 控制項](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
