---
title: "如何：使用設計工具格式化 Windows Form DataGrid 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da36f4f79d0016249dead686f305e1b93defceda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>如何：使用設計工具格式化 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。 色彩可以套用至資料列和資料行中。 資料列和資料行也可以隱藏或顯示自行斟酌。  
  
 有三個基本層面等的格式化<xref:System.Windows.Forms.DataGrid>控制項：  
  
-   您可以設定屬性，以建立資料會顯示為預設樣式。  
  
-   從該基底，您可以自訂某些資料表顯示在執行階段的方式。  
  
-   最後，您可以修改哪些資料行中的資料格，以及色彩顯示，並顯示的其他格式設定。  
  
 格式化資料格在初始步驟，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。 這些色彩和格式的選擇會形成從中您可以再進行變更，取決於資料的資料表和顯示的資料行的基底。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGrid>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。 在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**預設。 如需詳細資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>若要建立之預設樣式的 DataGrid 控制項  
  
1.  選取 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
2.  在**屬性**視窗中，設定下列屬性，視需要。  
  
    |屬性|說明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor`屬性定義的方格其偶數資料列的色彩。 當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>為不同的色彩屬性，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|而<xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性會決定外部資料列區域中，才看得見，由上至下，捲動方格時，或者如果只有少數資料列區域的色彩包含在方格中。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|就會立即顯示方格上方的方格視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|頂端的方格標題的字型。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|方格的視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|用來在方格中顯示文字的字型。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|資料格的資料列中的資料顯示的字型色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料格的格線色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|資料列和資料行的標頭的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|資料行標頭所使用的字型。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|會顯示方格的資料行標頭，包括資料行標頭文字和加號 （+） 和減號 （-） 展開和摺疊資料列，當多個相關資料表時，這些圖像的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|資料格，其中包含子資料表、 關聯性名稱和等等的連結中的所有連結的文字色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子資料表中，這會是父資料列的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子資料表中，這會是父資料列的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|判斷資料表和資料行名稱是否會顯示在父資料列，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 (單位為像素)。 重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設為小於 0。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|在方格中的資料列的資料列高度 （以像素為單位）。 重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設為小於 0。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|方格的資料列行首的寬度。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|選取的資料列或資料格時，這是背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|選取的資料列或資料格時，這是前景色彩。|  
  
    > [!NOTE]
    >  當您在自訂控制項的色彩時，便可將控制項設為不佳的色彩選擇 （例如，紅色和綠色） 而無法存取。 使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。  
  
     下列程序需要<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。 如需詳細資訊，請參閱[How to： 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>若要在設計階段設定資料表的資料的資料表和資料行樣式  
  
1.  選取<xref:System.Windows.Forms.DataGrid>控制項在表單上的。  
  
2.  在**屬性**視窗中，選取<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性，然後按一下**省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕。  
  
3.  在**DataGridTableStyle 集合編輯器**對話方塊中，按一下 **新增**將資料表樣式加入集合。  
  
     與**DataGridTableStyle 集合編輯器**、 您可以加入和移除資料表樣式，設定顯示和版面配置屬性，以及設定資料表樣式名稱對應。  
  
4.  設定<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性設為每個資料表樣式的對應名稱。  
  
     對應名稱用來指定應該用於哪一個資料表的資料表樣式。  
  
5.  在**DataGridTableStyle 集合編輯器**，選取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")).  
  
6.  在**DataGridColumnStyle 集合編輯器**對話方塊方塊中，為您建立的資料表樣式加入資料行樣式。  
  
     與**DataGridColumnStyle 集合編輯器**、 您可以加入和移除資料行樣式，設定顯示和版面配置屬性，以及設定對應名稱和資料行的資料格式字串。  
  
    > [!NOTE]
    >  如需格式化字串的詳細資訊，請參閱[格式化型別](../../../../docs/standard/base-types/formatting-types.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
