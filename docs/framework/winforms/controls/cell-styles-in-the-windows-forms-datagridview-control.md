---
title: "Windows Form DataGridView 控制項中的儲存格樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: edec8a00aff59195c6c80414eb4b950d68e488da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的儲存格樣式
每個資料格內<xref:System.Windows.Forms.DataGridView>控制項可以有它自己的樣式，例如，文字格式、 背景色彩、 前景色彩和字型。 通常，不過，多個資料格會共用特定的樣式特性。  
  
 群組的共用樣式的資料格可能包含特定的資料列或資料行，所有的資料格包含特定值或所有儲存格內的所有資料格控制項中。 這些群組重疊，因為每個資料格可能會收到多個位置的樣式設定資訊。 例如，您可能想每個資料格在<xref:System.Windows.Forms.DataGridView>控制項使用的相同字型，但只使用貨幣格式的貨幣資料行中的資料格和只有貨幣資料格具有負數使用紅色前景色彩。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle 類別  
 <xref:System.Windows.Forms.DataGridViewCellStyle>類別包含視覺化樣式相關的下列屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 這個類別也包含與格式相關的下列屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 如需有關這些屬性和其他儲存格樣式屬性的詳細資訊，請參閱<xref:System.Windows.Forms.DataGridViewCellStyle>參考文件和主題所列在 < 另請參閱下一節。  
  
## <a name="using-datagridviewcellstyle-objects"></a>使用 DataGridViewCellStyle 物件  
 您可以擷取<xref:System.Windows.Forms.DataGridViewCellStyle>物件的各種屬性從<xref:System.Windows.Forms.DataGridView>， <xref:System.Windows.Forms.DataGridViewColumn>， <xref:System.Windows.Forms.DataGridViewRow>，和<xref:System.Windows.Forms.DataGridViewCell>類別和其衍生的類別。 如果其中一個屬性具有尚未設定，擷取其值將會建立新<xref:System.Windows.Forms.DataGridViewCellStyle>物件。 也可以產生您自己<xref:System.Windows.Forms.DataGridViewCellStyle>物件，並將它們指派給這些屬性。  
  
 您可以避免不必要的樣式資訊複製共用<xref:System.Windows.Forms.DataGridViewCellStyle>物件多部<xref:System.Windows.Forms.DataGridView>項目。 因為在控制項、 資料行和資料列層級向下篩選至資料格層級的每個層級設定的樣式，您也可以藉由設定每個不同的層級上面的層級只有這些樣式屬性來避開樣式重複。 這是樣式繼承一節中詳細說明。  
  
 下表列出主屬性，取得或設定<xref:System.Windows.Forms.DataGridViewCellStyle>物件。  
  
|屬性|類別|說明|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView><xref:System.Windows.Forms.DataGridViewColumn>， <xref:System.Windows.Forms.DataGridViewRow>，和衍生類別|取得或設定整個控制項 （包括標題儲存格），資料行或資料列中的所有資料格所使用的預設樣式。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項中的所有資料列所使用的預設儲存格樣式。 這不包括標頭資料格。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定使用的替代控制項中的資料列的預設儲存格樣式。 用來建立類似 ledger 的效果。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料列標頭所使用的預設儲存格樣式。 如果已啟用視覺化樣式會覆寫目前的佈景主題。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料行標頭所使用的預設儲存格樣式。 如果已啟用視覺化樣式會覆寫目前的佈景主題。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>類別和衍生的類別|取得或設定指定資料格層級的樣式。 這些樣式會覆寫繼承自較高的層級。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell><xref:System.Windows.Forms.DataGridViewRow>， <xref:System.Windows.Forms.DataGridViewColumn>，和衍生類別|取得所有目前套用至資料格、 資料列或資料行，包括繼承自較高的層級的樣式的樣式。|  
  
 如上面所述，自動取得樣式屬性的值會具現化新<xref:System.Windows.Forms.DataGridViewCellStyle>如果屬性尚未先前設定的物件。 若要避免不必要地建立這些物件，資料列和資料類別都具有<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>屬性，您可以檢查以判斷是否<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>屬性已設定。 同樣地，資料格具有<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>屬性，指出是否<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性已設定。  
  
 每個樣式屬性都有對應*PropertyName* `Changed`事件<xref:System.Windows.Forms.DataGridView>控制項。 資料列、 資料行和資料格屬性，事件的名稱開頭為"`Row`"，"`Column`"，或 「`Cell`」 (比方說， <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>)。 每個事件發生時對應的樣式屬性設定為不同<xref:System.Windows.Forms.DataGridViewCellStyle>物件。 當您擷取時不會發生這些事件<xref:System.Windows.Forms.DataGridViewCellStyle>樣式屬性的物件，並修改其屬性值。 若要回應變更儲存格樣式物件本身，處理<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>事件。  
  
## <a name="style-inheritance"></a>樣式繼承  
 每個<xref:System.Windows.Forms.DataGridViewCell>取得它的外觀，從其<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性。 <xref:System.Windows.Forms.DataGridViewCellStyle>這個屬性所傳回的物件會繼承型別的屬性階層中的其值<xref:System.Windows.Forms.DataGridViewCellStyle>。 這些屬性如下所列的順序在<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>非標頭資料格取得其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>（僅適用於在奇數索引資料列中的資料格）  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 資料列和資料行的標頭資料格，<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性由從下列清單中指定的順序的來源屬性的值擴展。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 下圖說明此程序。  
  
 ![DataGridViewCellStyle 類型的](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 您也可以存取特定資料列和資料行所繼承的樣式。 資料行<xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>屬性會從下列屬性繼承其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 資料列<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>屬性會從下列屬性繼承其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>（僅適用於在奇數索引資料列中的資料格）  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 中每一個屬性<xref:System.Windows.Forms.DataGridViewCellStyle>所傳回物件`InheritedStyle`屬性，屬性值取自適當有對應的屬性不是設為值的清單中的第一個儲存格樣式<xref:System.Windows.Forms.DataGridViewCellStyle>類別的預設值。  
  
 下表將說明如何<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>範例資料格的屬性值都繼承自其包含的資料行。  
  
|類型的屬性`DataGridViewCellStyle`|範例`ForeColor`擷取物件的值|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 在此情況下，<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>從儲存格的資料列的值是在清單上的第一個實際值。 這會變成<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>屬性值的儲存格的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>。  
  
 下圖說明不同<xref:System.Windows.Forms.DataGridViewCellStyle>屬性可以繼承其值的不同位置。  
  
 ![DataGridView 屬性 &#45; 值繼承](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 利用樣式繼承，您可以提供適當的樣式整個控制項而不需要在多個位置指定相同的資訊。  
  
 標頭資料格會參與樣式繼承所述，雖然所傳回的物件<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項有覆寫所傳回的物件的屬性值的初始屬性值<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性。 如果要讓屬性所傳回的物件設定<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性套用至資料列和資料行標頭，您必須設定對應的屬性所傳回的物件<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>指示內容設為預設值如<xref:System.Windows.Forms.DataGridViewCellStyle>類別。  
  
> [!NOTE]
>  如果已啟用視覺化樣式，資料列和資料行標頭 (除了<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) 的樣式會自動根據目前的佈景主題，並覆寫這些屬性所指定的任何樣式。  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>， <xref:System.Windows.Forms.DataGridViewImageColumn>，和<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>類型也會初始化的資料行所傳回之物件的某些值<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性。 如需詳細資訊，請參閱這些類型的參考文件。  
  
## <a name="setting-styles-dynamically"></a>動態設定樣式  
 若要自訂的特定值的資料格的樣式，實作的處理常式<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 此事件處理常式會接收的引數<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>型別。 此物件包含可讓您決定的位置中以及正在格式化儲存格的值的屬性<xref:System.Windows.Forms.DataGridView>控制項。 此物件也包含<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>屬性初始化為值的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>正在格式化資料格的屬性。 您可以修改儲存格樣式屬性，指定適當的資料格的值和位置的樣式資訊。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint>和<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件也會收到<xref:System.Windows.Forms.DataGridViewCellStyle>物件在事件資料，但在他們的情況下，它是資料列的複本<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>唯讀用途，而且它會變更的屬性不會影響控制項。  
  
 您可以也會動態修改為了回應事件的個別儲存格的樣式例如<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType>和<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件。 比方說，在處理常式中<xref:System.Windows.Forms.DataGridView.CellMouseEnter>事件，您可以儲存的資料格的背景色彩的目前值 (透過儲存格的擷取<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性)，然後將它設定為新的會反白顯示資料格時滑鼠停留色彩。 中的處理常式<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件，您接著可以還原的背景色彩為原始值。  
  
> [!NOTE]
>  快取儲存在儲存格的值<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性是非常重要，不論設定特定的樣式值。 如果您暫時取代樣式設定，將其還原至其原始的 「 未設定 」 狀態可確保，資料格會回到繼承較高層級的樣式設定。 如果您需要決定作用中的儲存格值，不管是否繼承樣式的實際樣式，請使用儲存格的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [操作說明：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
