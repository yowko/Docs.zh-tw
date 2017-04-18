---
title: "DataGrid 控制項中的調整大小選項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動調整 DataGrid 的大小"
  - "DataGrid 控制項 [WPF], 調整大小"
  - "大小 [WPF], DataGrid"
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DataGrid 控制項中的調整大小選項
您可以使用各種選項來控制 <xref:System.Windows.Controls.DataGrid> 調整大小的方式。  <xref:System.Windows.Controls.DataGrid> 以及 <xref:System.Windows.Controls.DataGrid> 中個別的資料列和資料行都可以設定成依內容自動調整大小，或是設定成特定的值。  根據預設，<xref:System.Windows.Controls.DataGrid> 會配合其內容大小擴增及縮減。  
  
## 調整 DataGrid 大小  
  
### 使用自動調整大小的注意事項  
 根據預設，<xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性會設定為 <xref:System.Double.NaN?displayProperty=fullName> \(在 XAML 中則為 "`Auto`"\)，而且 <xref:System.Windows.Controls.DataGrid> 會調整成其內容的大小。  
  
 當放在沒有限制子系大小的容器 \(Container\) 內 \(例如 <xref:System.Windows.Controls.Canvas> 或 <xref:System.Windows.Controls.StackPanel>\) 時，<xref:System.Windows.Controls.DataGrid> 將會延伸到容器的可見範圍之外，而且不會顯示捲軸。  這個情況對使用性和效能都有影響。  
  
 當繫結至資料集時，如果 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.FrameworkElement.Height%2A> 不受限制，它會繼續為繫結資料集中的每個資料項目加入資料列。  這可能會讓 <xref:System.Windows.Controls.DataGrid> 隨著資料列的加入而擴增到超出應用程式的可見範圍之外。  <xref:System.Windows.Controls.DataGrid> 在這種情況下並不會顯示捲軸，因為它的 <xref:System.Windows.FrameworkElement.Height%2A> 還會繼續增加，以容納新的資料列。  
  
 系統會為 <xref:System.Windows.Controls.DataGrid> 中的每個資料列建立一個物件。  如果您處理的資料集規模較大，而且允許 <xref:System.Windows.Controls.DataGrid> 自動調整大小，建立大量物件可能會影響應用程式的效能。  
  
 為了避免在處理大型資料集時發生這些問題，建議您明確設定 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.FrameworkElement.Height%2A>，或是將它放在 <xref:System.Windows.FrameworkElement.Height%2A> 受到限制的容器中，例如 <xref:System.Windows.Controls.Grid>。  當 <xref:System.Windows.FrameworkElement.Height%2A> 受到限制時，<xref:System.Windows.Controls.DataGrid> 只會建立符合其指定 <xref:System.Windows.FrameworkElement.Height%2A> 的資料列，而且會視需要回收這些資料列來顯示新的資料。  
  
### 設定 DataGrid 大小  
 <xref:System.Windows.Controls.DataGrid> 可以設定成自動在指定的界限範圍內調整大小，或者您也可以將 <xref:System.Windows.Controls.DataGrid> 設定成特定大小。  下表顯示可以設定以控制 <xref:System.Windows.Controls.DataGrid> 大小的屬性。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的特定高度。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的高度上限。  <xref:System.Windows.Controls.DataGrid> 將垂直成長到這個高度為止。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的高度下限。  <xref:System.Windows.Controls.DataGrid> 將垂直縮減到這個高度為止。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的特定寬度。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的寬度上限。  <xref:System.Windows.Controls.DataGrid> 將水平成長到這個寬度為止。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|設定 <xref:System.Windows.Controls.DataGrid> 的寬度下限。  <xref:System.Windows.Controls.DataGrid> 將水平縮減到這個寬度為止。|  
  
## 調整資料列和資料列行首大小  
  
### DataGrid 資料列  
 根據預設，<xref:System.Windows.Controls.DataGrid> 資料列的 <xref:System.Windows.FrameworkElement.Height%2A> 屬性會設定為 <xref:System.Double.NaN?displayProperty=fullName> \(在 XAML 中則為 "`Auto`"\)，而且資料列高度會擴展成其內容的大小。  <xref:System.Windows.Controls.DataGrid> 控制項中所有資料列的高度都可透過設定 <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=fullName> 屬性來指定。  使用者能以拖曳資料列行首分隔線的方式來變更資料列高度。  
  
### DataGrid 資料列行首  
 若要顯示資料列行首，<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 屬性必須設定為 <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName>。  預設會顯示資料列行首，且會配合其內容自動調整大小。  您可透過設定 <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=fullName> 屬性，為資料列行首指定特定寬度。  
  
## 調整資料行和資料行行首大小  
  
### DataGrid 資料行  
 <xref:System.Windows.Controls.DataGrid> 會使用 <xref:System.Windows.Controls.DataGridLength> 和 <xref:System.Windows.Controls.DataGridLengthUnitType> 結構的值來指定絕對或自動調整大小模式。  
  
 下表顯示 <xref:System.Windows.Controls.DataGridLengthUnitType> 結構提供的值。  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|預設自動調整大小模式會根據儲存格和資料行行首的內容來調整 <xref:System.Windows.Controls.DataGrid> 資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|儲存格架構自動調整大小模式會根據資料行中儲存格的內容 \(不包括資料行行首\) 來調整 <xref:System.Windows.Controls.DataGrid> 資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|行首架構自動調整大小模式只會根據資料行行首的內容來調整 <xref:System.Windows.Controls.DataGrid> 資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|像素架構調整大小模式會根據提供的數值來調整 <xref:System.Windows.Controls.DataGrid> 資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|星號調整大小模式是用於依照加權比例配置可用空間。<br /><br /> 在 XAML 中，星號值是以 n\* 表示，其中 n 代表數值。  1\* 就等於 \*。  例如，如果 <xref:System.Windows.Controls.DataGrid> 中兩個資料行的寬度為 \* 和 2\*，第一個資料行就會收到一個部分的可用空間，而第二個資料行則會收到兩個部分的可用空間。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> 類別可以用來在數值或字串值以及 <xref:System.Windows.Controls.DataGridLength> 值之間轉換資料。  
  
 根據預設，<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName> 屬性設定為 <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>，而且 <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName> 屬性設定為 <xref:System.Windows.Controls.DataGridLength.Auto%2A>。  當調整大小模式設定為 <xref:System.Windows.Controls.DataGridLength.Auto%2A> 或 <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> 時，資料行將擴增為其最寬的可見內容之寬度。  捲動時，如果大於目前資料行大小的內容捲動到檢視中，這些調整大小模式將會讓資料行擴大。  當內容捲動到檢視範圍之外時，資料行並不會縮小。  
  
 <xref:System.Windows.Controls.DataGrid> 中的資料行也可以設定為只在指定的界限內自動調整大，或者您可以將資料行設定為特定大小。  下表顯示可以設定以控制資料行大小的屬性。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName>|設定 <xref:System.Windows.Controls.DataGrid> 中所有資料行的上限。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=fullName>|設定個別資料行的上限。  覆寫 <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName>。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName>|設定 <xref:System.Windows.Controls.DataGrid> 中所有資料行的下限。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=fullName>|設定個別資料行的下限。  覆寫 <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName>。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName>|設定 <xref:System.Windows.Controls.DataGrid> 中所有資料行的特定寬度。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName>|設定個別資料行的特定寬度。  覆寫 <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName>。|  
  
### DataGrid 資料行行首  
 預設會顯示 <xref:System.Windows.Controls.DataGrid> 資料行行首。  若要隱藏資料行行首，必須將 <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 屬性設定為 <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName>。  當顯示資料行行首時，預設會配合其內容自動調整大小。  您可透過設定 <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=fullName> 屬性，為資料行行首指定特定高度。  
  
### 使用滑鼠調整大小  
 使用者可以透過拖曳資料列或資料行行首分隔線，來調整 <xref:System.Windows.Controls.DataGrid> 資料列和資料行的大小。  <xref:System.Windows.Controls.DataGrid> 也支援以按兩下資料列或資料行行首分隔線的方式，自動調整資料列和資料行的大小。  若要防止使用者調整特定資料行的大小，請針對個別資料行，將 <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> 屬性設定為 `false`。  若要防止使用者調整所有資料行的大小，請將 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> 設定為 `false`。  若要防止使用者調整所有資料列的大小，請將 <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=fullName> 屬性設定為 `false`。  
  
## 請參閱  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGridColumn>   
 <xref:System.Windows.Controls.DataGridLength>   
 <xref:System.Windows.Controls.DataGridLengthConverter>