---
title: "如何：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a3c7422bc83c7ee1f09bac05333799708cd2f2f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項
您可以使用設計工具來連接<xref:System.Windows.Forms.DataGridView>多種不同的不同，包括資料庫、 商務物件或 Web 服務的資料來源的控制項。 控制當您將控制項繫結至資料來源，使用設計工具時，自動繫結至<xref:System.Windows.Forms.BindingSource>代表資料來源的元件。 此外，控制項中會自動產生資料行，以符合資料來源所提供的結構描述資訊。  
  
 產生資料行之後，您可加以修改以符合您的需求。 例如，您可以移除或隱藏您不想顯示的資料行、可以重新排列資料行，或者可以修改資料行類型。 如需修改資料行的詳細資訊，請參閱＜另請參閱＞一節中所列的主題。  
  
 您也可以繫結多個<xref:System.Windows.Forms.DataGridView>控制項加入相關資料表來建立主從式關聯性。 在此組態中，一個控制項會顯示父資料表，而另一個控制項只會顯示子資料表中與父資料表中的目前資料列相關的資料列。 如需詳細資訊，請參閱[如何：在 Windows Forms 應用程式中顯示相關的資料](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項或主要/詳細資料關聯性的兩個控制項。 如需啟動這類專案的相關資訊，請參閱[如何︰建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[如何︰將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-bind-the-control-to-a-data-source"></a>將控制項繫結至資料來源  
  
1.  按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項。  
  
2.  按一下 [選擇資料來源] 選項的下拉式箭號。  
  
3.  如果您的專案還沒有資料來源，請按一下 [新增專案資料來源] 並遵循精靈所指示的步驟。  
  
     如需詳細資訊，請參閱[資料來源設定精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。 新的資料來源會出現在 [選擇資料來源] 下拉式視窗中。 如果新的資料來源只包含一個成員，例如單一資料庫資料表，則控制項會自動繫結至該成員。 否則請繼續下一個步驟。  
  
4.  如果 [其他資料來源] 和 [專案資料來源] 節點尚未展開，請加以展開，然後選取控制項所要繫結的資料來源。  
  
5.  如果您的資料來源包含多個成員，例如，如果您已建立<xref:System.Data.DataSet?displayProperty=nameWithType>，其中包含多個資料表，依序展開 資料來源，然後選取 繫結至特定的成員。  
  
6.  若要在建立主從式關聯性**選擇資料來源**第二個下拉式視窗<xref:System.Windows.Forms.DataGridView>控制中，展開<xref:System.Windows.Forms.BindingSource>建立父資料表，並從清單中選取相關的子系資料表顯示。  
  
    > [!NOTE]
    >  如果專案已經有資料來源，您也可以使用 [資料來源] 視窗建立資料表單。 如需詳細資訊，請參閱[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [如何：連接至資料庫中的資料](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [操作說明：使用設計工具變更 Windows Forms DataGridView 控制項中資料行的順序](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [操作說明：使用設計工具變更 Windows Forms DataGridView 資料行的類型](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [操作說明：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [操作說明：使用設計工具隱藏 Windows Forms DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [操作說明：使用設計工具將 Windows Forms DataGridView 控制項中的資料行設為唯讀](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [如何：在 Windows Forms 應用程式中顯示相關的資料](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
