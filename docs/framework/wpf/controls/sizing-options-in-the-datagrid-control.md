---
title: DataGrid 控制項中的調整大小選項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4219dc88a263b73aa89812a2f841a920c804796b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid 控制項中的調整大小選項
各種選項可用來控制如何<xref:System.Windows.Controls.DataGrid>調整大小。 <xref:System.Windows.Controls.DataGrid>，個別的資料列和資料行中的<xref:System.Windows.Controls.DataGrid>、 可以設定為其內容自動調整大小，或可以設定為特定值。 根據預設，<xref:System.Windows.Controls.DataGrid>會成長並縮小為容納其內容的大小。  
  
## <a name="sizing-the-datagrid"></a>調整大小的 DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>使用自動調整大小的注意事項  
 根據預設，<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>屬性<xref:System.Windows.Controls.DataGrid>設為<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`"在 XAML 中)，而<xref:System.Windows.Controls.DataGrid>會調整到其內容的大小。  
  
 放置於不會限制大小的子系，例如容器時，<xref:System.Windows.Controls.Canvas>或<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.DataGrid>會自動縮放可見的容器界限之外，並不會顯示捲軸。 這種情況有可用性和效能的影響。  
  
 當繫結至資料集，如果<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Controls.DataGrid>是不受限制，它將會繼續為每個資料項目的資料列加入繫結的資料集內。 這可能會造成<xref:System.Windows.Controls.DataGrid>成長的應用程式顯示範圍之外，資料列加入。 <xref:System.Windows.Controls.DataGrid>不會顯示捲軸在此情況下因為其<xref:System.Windows.FrameworkElement.Height%2A>仍將會成長以容納新資料列。  
  
 每個資料列中建立物件<xref:System.Windows.Controls.DataGrid>。 如果您使用大型資料集，而您允許<xref:System.Windows.Controls.DataGrid>自動調整本身大小，建立大量的物件可能會影響您的應用程式的效能。  
  
 若要避免這些問題，當您使用大型資料集時，建議您使用特別設定<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Controls.DataGrid>或將它放在容器，以限制其<xref:System.Windows.FrameworkElement.Height%2A>，例如<xref:System.Windows.Controls.Grid>。 當<xref:System.Windows.FrameworkElement.Height%2A>限制，<xref:System.Windows.Controls.DataGrid>才會建立可容納其指定的資料列<xref:System.Windows.FrameworkElement.Height%2A>，並視需要顯示新的資料，就會回收資料列。  
  
### <a name="setting-the-datagrid-size"></a>設定資料格大小  
 <xref:System.Windows.Controls.DataGrid>可以設定為自動在指定的界限內的大小或<xref:System.Windows.Controls.DataGrid>可以設定為特定的大小。 下表顯示可以將控制項的屬性<xref:System.Windows.Controls.DataGrid>大小。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|設定特定高度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|設定的高度上限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid>將垂直成長，直到達到此高度。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|設定的高度下限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid>直到達到這個高度會垂直縮小。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|設定特定寬度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|設定的寬度上限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid>直到達到此寬度會以水平方式成長。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|設定的寬度下限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid>直到達到此寬度會水平縮小。|  
  
## <a name="sizing-rows-and-row-headers"></a>調整資料列和資料列標頭  
  
### <a name="datagrid-rows"></a>DataGrid 的資料列  
 根據預設，<xref:System.Windows.Controls.DataGrid>資料列的<xref:System.Windows.FrameworkElement.Height%2A>屬性設定為<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`」 在 XAML 中)，以及資料列高度，將展開到其內容的大小。 中的所有資料列的高度<xref:System.Windows.Controls.DataGrid>可以設定來指定<xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType>屬性。 使用者可以變更資料列高度，拖曳資料列行首分割線。  
  
### <a name="datagrid-row-headers"></a>DataGrid 資料列標頭  
 若要顯示資料列標頭<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>屬性必須設定為<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>或<xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>。 根據預設，會顯示資料列標頭，並自動調整大小以符合其內容。 資料列標頭可以藉由設定指定了特定寬度<xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType>屬性。  
  
## <a name="sizing-columns-and-column-headers"></a>調整資料行和資料行標頭  
  
### <a name="datagrid-columns"></a>DataGrid 資料行  
 <xref:System.Windows.Controls.DataGrid>會使用值<xref:System.Windows.Controls.DataGridLength>和<xref:System.Windows.Controls.DataGridLengthUnitType>結構，以指定絕對或自動調整大小模式。  
  
 下表顯示所提供的值<xref:System.Windows.Controls.DataGridLengthUnitType>結構。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|自動調整大小模式大小預設<xref:System.Windows.Controls.DataGrid>儲存格和資料行標頭的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|資料格為基礎的自動調整大小模式大小<xref:System.Windows.Controls.DataGrid>資料行，不包含資料行標頭中的儲存格的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|標頭為基礎的自動調整大小模式大小<xref:System.Windows.Controls.DataGrid>只資料行行首的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|以像素為基礎調整大小模式大小<xref:System.Windows.Controls.DataGrid>根據所提供之數值的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星型的調整大小模式用以分散可用空間的加權比例。<br /><br /> 在 XAML 中、 星狀的值會表示為 n * 其中 n 代表一個數字值。 1\*相當於\*。 比方說，如果兩個資料行中的<xref:System.Windows.Controls.DataGrid>有寬度\*和 2\*、 第一欄將會收到的可用空間的一個部分和第二欄會接收兩個部分的可用空間。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>類別可以用來轉換數值或字串值之間的資料和<xref:System.Windows.Controls.DataGridLength>值。  
  
 根據預設，<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>屬性設定為<xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>，而<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>屬性設定為<xref:System.Windows.Controls.DataGridLength.Auto%2A>。 當調整大小模式設定為<xref:System.Windows.Controls.DataGridLength.Auto%2A>或<xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>，資料行成長後將其 widest 可見內容的寬度。 如果向下捲動，這些調整大小模式會讓資料行以展開如果內容大於目前的資料行大小捲動到檢視的。 內容捲動到檢視之後，將不會縮減資料行。  
  
 中的資料行<xref:System.Windows.Controls.DataGrid>也可以設定為自動只在指定的界限內的大小或資料行可以設定為特定的大小。 下表顯示可以設定來控制資料行大小的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|設定中的所有資料行上限<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|設定個別資料行的上限。 覆寫<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|設定中的所有資料行的下限<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|設定個別資料行的下限。 覆寫<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|設定所有的資料行中的特定寬度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|設定個別資料行的寬度。 覆寫<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>。|  
  
### <a name="datagrid-column-headers"></a>DataGrid 資料行標頭  
 根據預設，<xref:System.Windows.Controls.DataGrid>資料行標頭會顯示。 若要隱藏資料行標頭，<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>屬性必須設定為<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>或<xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>。 根據預設，當顯示資料行標頭時，自動調整大小以符合其內容。 資料行標頭可以藉由設定指定特定高度<xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType>屬性。  
  
### <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 使用者可以調整大小<xref:System.Windows.Controls.DataGrid>資料列和資料行，拖曳資料行或資料列行首分割線。 <xref:System.Windows.Controls.DataGrid>也支援自動調整大小的資料列和資料行按兩下資料列或資料行行首分割線。 若要防止使用者調整特定資料行大小，將<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>屬性`false`個別資料行。 若要防止使用者調整所有資料行大小，請設定<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>屬性`false`。 若要防止使用者調整所有資料列，將<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType>屬性`false`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>
