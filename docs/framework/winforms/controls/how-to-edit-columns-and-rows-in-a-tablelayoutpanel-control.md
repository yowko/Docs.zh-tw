---
title: "如何：編輯 TableLayoutPanel 控制項中的資料行和資料列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75b83a2d7475f1a01d80c82013dac519edc4de08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>如何：編輯 TableLayoutPanel 控制項中的資料行和資料列
您可以使用集合編輯器 的<xref:System.Windows.Forms.TableLayoutPanel>控制項稱為**資料行和資料列樣式**對話方塊中，若要編輯的資料列和資料行的控制項。  
  
> [!NOTE]
>  如果您想要跨多個資料列或資料行的控制項時，設定`RowSpan`和`ColumnSpan`控制項的屬性。 如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  如果您想要在儲存格時，將控制項對齊，或者您想要自動縮放儲存格內的控制項，請使用控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性。 如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-edit-rows-and-columns"></a>若要編輯的資料列和資料行  
  
1.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
2.  按一下<xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 並選取**編輯資料列和資料行**開啟**資料行和資料列樣式** 對話方塊。 您也可以以滑鼠右鍵按一下<xref:System.Windows.Forms.TableLayoutPanel>控制，然後選取**編輯資料列和資料行**從捷徑功能表。  
  
3.  若要新增或移除資料行，選取**資料行**從**成員型別**下拉式清單方塊。  
  
4.  若要新增或移除資料列，選取**列**從**成員型別**下拉式清單方塊。  
  
5.  按一下**新增**按鈕，將資料列或資料行加入至結尾**成員**清單。  
  
6.  按一下**插入**按鈕在清單中加入資料列或資料行的目前選取的項目之前。  
  
7.  如果您要新增的資料列或資料行，選取**大小類型**新的資料列或資料行。 如需詳細資訊，請參閱<xref:System.Windows.Forms.SizeType>。  
  
8.  若要移除的資料列或資料行，請按一下**移除**按鈕來刪除目前選取的項目中**成員**清單。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.SizeType>  
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
