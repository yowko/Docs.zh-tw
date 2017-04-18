---
title: "Windows Form DataGridView 控制項中的儲存格樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "儲存格, 樣式"
  - "資料格, 儲存格樣式"
  - "DataGridView 控制項 [Windows Form], 儲存格樣式"
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Windows Form DataGridView 控制項中的儲存格樣式
<xref:System.Windows.Forms.DataGridView> 控制項內的每個儲存格都可擁有自己的樣式，例如文字格式、背景色彩、前景色彩和字型。  不過，一般來說會有多個儲存格共用特定的樣式特性。  
  
 共用樣式的儲存格群組可能包括特定資料列或資料行內的所有儲存格、包含特定值的所有儲存格或控制項中的所有儲存格。  由於這些群組重疊，所以每個儲存格可能可以從一個以上的位置取得樣式設定資訊。  例如，您可能會想要 <xref:System.Windows.Forms.DataGridView> 控制項的每個儲存格都使用相同的字型，而只有貨幣資料行中的儲存格採用貨幣格式，同時也只有負數的貨幣儲存格使用紅色前景色彩。  
  
## DataGridViewCellStyle 類別  
 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別包含以下與視覺化樣式相關的屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 這個類別也包含以下與格式設定相關的屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 如需這些屬性和其他儲存格樣式屬性的詳細資訊，請參閱 <xref:System.Windows.Forms.DataGridViewCellStyle> 參考文件以及底下＜請參閱＞一節中所列出的主題。  
  
## 使用 DataGridViewCellStyle 物件  
 您可以從 <xref:System.Windows.Forms.DataGridView> 類別、<xref:System.Windows.Forms.DataGridViewColumn> 類別、<xref:System.Windows.Forms.DataGridViewRow> 類別、<xref:System.Windows.Forms.DataGridViewCell> 類別和前四個類別的衍生類別 \(Derived Class\) 透過這些類別的各種屬性來擷取 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件。  如果這些屬性中有任何一個尚未設定，擷取這個未設定的屬性值時會建立新的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件。  也可以產生 \(Instantiate\) 自己的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，然後將它們指派給這些屬性。  
  
 您可以在多個 <xref:System.Windows.Forms.DataGridView> 項目之中共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，如此一來樣式資訊即可避免不必要的重複。  由於在控制項、資料行和資料列層級上設定的樣式會從該層級向下篩選至儲存格層級，為了避免樣式重複，可以在每個層級上只設定與上個層級不同的樣式屬性。  關於這點在接下來的＜樣式繼承＞一節中有更詳盡的描述。  
  
 下表列出會取得或設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件的主要屬性。  
  
|屬性|類別|描述|  
|--------|--------|--------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、<xref:System.Windows.Forms.DataGridViewColumn>、<xref:System.Windows.Forms.DataGridViewRow> 和衍生類別|取得或設定預設樣式，此樣式用於整個控制項中的所有儲存格 \(包括標題儲存格\)、資料行中的所有儲存格，或資料列中的所有儲存格。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定預設的儲存格樣式，此樣式用於控制項中的所有資料列。  這裡並不包括標題儲存格。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定預設的儲存格樣式，此樣式用於控制項中的替代資料列。  用以產生類似 Ledger 的效果。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定預設的儲存格樣式，此樣式用於控制項的資料列行首。  如果已啟用視覺化樣式，則將由目前主題進行覆寫。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定預設的儲存格樣式，此樣式用於控制項的資料行行首。  如果已啟用視覺化樣式，則將由目前主題進行覆寫。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> 和衍生類別|取得或設定在儲存格層級上指定的樣式。  這些樣式會覆寫繼承自較高層級的樣式。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewRow>、<xref:System.Windows.Forms.DataGridViewColumn> 和衍生類別|取得目前套用至儲存格、資料列或資料行的所有樣式 \(包括繼承自較高層級的樣式\)。|  
  
 如上所述，如果樣式屬性之前尚未設定，則在取得該屬性值時將會自動產生新的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件。  若要避免建立不必要的物件，可以檢查資料列類別和資料行類別中的 <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> 屬性，以便判斷 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> 屬性是否已經設定。  同樣地，儲存格類別也有 <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> 屬性，指出 <xref:System.Windows.Forms.DataGridViewCell.Style%2A> 屬性是否已經設定。  
  
 每個樣式屬性在 <xref:System.Windows.Forms.DataGridView> 控制項上都有對應的 *PropertyName*`Changed` 事件。  對於資料列屬性、資料行屬性和儲存格屬性而言，此事件的名稱是以 "`Row`"、"`Column`" 或 "`Cell`" 開頭 \(例如，<xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>\)。  當對應的樣式屬性設定為不同的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件時，會發生這個事件。  當從樣式屬性擷取 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件並修改它的屬性值時，並不會發生這些事件。  若要回應儲存格樣式物件本身的變更，請處理 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> 事件。  
  
## 樣式繼承  
 每個 <xref:System.Windows.Forms.DataGridViewCell> 都可從它的 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 屬性取得外觀。  這個屬性所傳回的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件其值是繼承自 <xref:System.Windows.Forms.DataGridViewCellStyle> 型別的屬性階層架構。  下列屬性是依非標題儲存格的 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 取得其值的順序而排列。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(僅適用於索引編號為單數的資料列的儲存格\)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 對於資料列和資料行的標題儲存格而言，<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 屬性會按下列來源屬性清單的順序，填入各值。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 下列圖表說明這個程序。  
  
 ![DataGridViewCellStyle 類型的屬性](../../../../docs/framework/winforms/controls/media/datagridviewcells1.png "DataGridViewCells1")  
  
 您也可以存取特定資料列和資料行所繼承的樣式。  資料行的 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> 屬性是從下列屬性繼承其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 資料列的 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> 屬性是從下列屬性繼承其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(僅適用於索引編號為單數的資料列的儲存格\)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 對於 `InheritedStyle` 屬性所傳回的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件中的每個屬性而言，屬性值是從適當清單中的第一個儲存格樣式取得，此份清單可讓對應的屬性設定為 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別預設值以外的值。  
  
 下表說明如何從範例儲存格的包含資料行繼承該儲存格的 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 屬性值。  
  
|`DataGridViewCellStyle` 型別的屬性|擷取物件 \(Retrieved Object\) 的範例 `ForeColor` 值|  
|-----------------------------------|-------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Red%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Black%2A?displayProperty=fullName>|  
  
 在這種情況下，該儲存格資料行的 <xref:System.Drawing.Color.Red%2A?displayProperty=fullName> 值是清單上的第一個實際值。  這會成為儲存格的 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 屬性值。  
  
 下圖說明不同的 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性如何才能從不同的位置繼承它們的值。  
  
 ![DataGridView 屬性值繼承](../../../../docs/framework/winforms/controls/media/datagridviewcells2.png "DataGridViewCells2")  
  
 善用樣式繼承的特點，您可以提供適用於整個控制項的樣式，而不需要在多個位置指定相同的資訊。  
  
 雖然標題儲存格依所述加入樣式繼承，但由 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> 屬性所傳回的物件會有初始屬性值，此值會覆寫由 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性傳回的物件的屬性值。  如果想要將 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性所傳回的物件的屬性套用至資料列行首和資料行行首，必須將 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> 屬性所傳回的物件的對應屬性設定為指定給 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的預設值。  
  
> [!NOTE]
>  如果已啟用視覺化樣式，目前的主題會自動設定資料列行首和資料行行首 \(不包括 <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>\) 的樣式，覆寫這些屬性所指定的任何樣式。  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>、<xref:System.Windows.Forms.DataGridViewImageColumn> 和 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> 型別也會初始化資料行 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性所傳回的物件的部分值。  如需詳細資訊，請參閱這些型別的參考文件。  
  
## 動態設定樣式  
 若要以特定值來自訂儲存格的樣式，請實作 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> 事件的處理常式。  這個事件處理常式會接收 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 型別的引數。  這個物件包含可讓您判斷格式化的儲存格值以及此儲存格在 <xref:System.Windows.Forms.DataGridView> 控制項中的位置的屬性。  這個物件也包含 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> 屬性，此屬性會初始化正在格式化的儲存格的 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 屬性值。  您可以修改儲存格樣式屬性，以指定適合此儲存格值和位置的樣式資訊。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint> 事件也會接收事件資料中的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，但在這兩個情況中，此物件是資料列 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> 屬性的唯讀複本，而且它的變更並不會影響控制項。  
  
 您也可以動態修改個別儲存格的樣式以回應例如 <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=fullName> 和 <xref:System.Windows.Forms.DataGridView.CellMouseLeave> 等事件。  例如，在 <xref:System.Windows.Forms.DataGridView.CellMouseEnter> 事件處理常式中，您可以儲存目前的儲存格背景色彩的值 \(透過該儲存格的 <xref:System.Windows.Forms.DataGridViewCell.Style%2A> 屬性擷取\)，接著將此值設定為另一新色彩，當滑鼠停留在儲存格上時，會使用此新色彩來反白顯示該儲存格。  接著可在 <xref:System.Windows.Forms.DataGridView.CellMouseLeave> 事件處理常式中，將背景色彩復原為原始值。  
  
> [!NOTE]
>  無論是否已設定特定樣式值，快取儲存格的 <xref:System.Windows.Forms.DataGridViewCell.Style%2A> 屬性中所儲存的值，都是一項重要的操作。  如果您是暫時取代某個樣式設定，那麼將樣式設定復原成原來的「未設定」狀態，可確保儲存格恢復從較高層級繼承樣式設定。  如果需要判斷某個儲存格的現用實際樣式，不論該樣式是否為繼承而來的，都要使用儲存格的 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 屬性。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)