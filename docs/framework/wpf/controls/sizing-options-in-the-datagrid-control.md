---
title: DataGrid 控制項中的調整大小選項
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970985"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid 控制項中的調整大小選項
各種選項可用來控制如何<xref:System.Windows.Controls.DataGrid>調整大小。 <xref:System.Windows.Controls.DataGrid>，及個別的資料列和資料行中的<xref:System.Windows.Controls.DataGrid>、 可以設定為其內容自動調整大小，或可以設為特定值。 根據預設，<xref:System.Windows.Controls.DataGrid>會成長，並縮小為容納其內容的大小。  
  
## <a name="sizing-the-datagrid"></a>調整大小的 DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>使用自動調整大小的注意事項  
 根據預設，<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>的屬性<xref:System.Windows.Controls.DataGrid>設為<xref:System.Double.NaN?displayProperty=nameWithType>(「`Auto`」 在 XAML 中)，和<xref:System.Windows.Controls.DataGrid>將調整，以其內容的大小。  
  
 當沒有這類限制的大小及其子系，在容器內放置<xref:System.Windows.Controls.Canvas>或<xref:System.Windows.Controls.StackPanel>，則<xref:System.Windows.Controls.DataGrid>會顯示容器的界限外而且不會顯示捲軸。 這種情況有可用性和效能的影響。  
  
 當繫結至資料集，如果<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Controls.DataGrid>是不受限制，它會繼續在繫結的資料集新增每個資料項目的資料列。 這可能會造成<xref:System.Windows.Controls.DataGrid>成長至超出您的應用程式的可見範圍加入資料列時。 <xref:System.Windows.Controls.DataGrid>因為不會顯示捲軸在此情況下其<xref:System.Windows.FrameworkElement.Height%2A>將會繼續成長以容納新的資料列。  
  
 每個資料列建立物件<xref:System.Windows.Controls.DataGrid>。 如果您正在使用大型資料集，而且您允許<xref:System.Windows.Controls.DataGrid>自動調整本身大小，建立大量的物件可能會影響您的應用程式的效能。  
  
 若要避免這些問題，當您使用大型資料集時，建議明確設定<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Controls.DataGrid>或將它放入容器，以限制其<xref:System.Windows.FrameworkElement.Height%2A>，例如<xref:System.Windows.Controls.Grid>。 當<xref:System.Windows.FrameworkElement.Height%2A>受限制，<xref:System.Windows.Controls.DataGrid>才會建立可容納其指定的資料列<xref:System.Windows.FrameworkElement.Height%2A>，並視需要顯示新的資料，就會回收資料列。  
  
### <a name="setting-the-datagrid-size"></a>設定資料格大小  
 <xref:System.Windows.Controls.DataGrid>可以設定為自動在指定的界限內的大小或<xref:System.Windows.Controls.DataGrid>可以設定為特定的大小。 下表顯示可以設定來控制內容<xref:System.Windows.Controls.DataGrid>大小。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|設定特定高度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|設定的高度上限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid>會垂直成長，直到它到達此高度。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|設定的高度下限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid> ，直到它到達此高度會垂直縮小。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|設定特定寬度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|設定的寬度上限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid> ，直到它到達此寬度會以水平方式成長。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|設定的寬度下限<xref:System.Windows.Controls.DataGrid>。 <xref:System.Windows.Controls.DataGrid> ，直到它到達此寬度會以水平方式壓縮。|  
  
## <a name="sizing-rows-and-row-headers"></a>調整資料列和資料列標頭  
  
### <a name="datagrid-rows"></a>DataGrid Rows  
 根據預設，<xref:System.Windows.Controls.DataGrid>資料列的<xref:System.Windows.FrameworkElement.Height%2A>屬性設定為<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`」 在 XAML 中)，資料列高度會展開其內容的大小。 中的所有資料列的高度<xref:System.Windows.Controls.DataGrid>可以設定來指定<xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType>屬性。 使用者可以拖曳資料列行首分割線，以變更資料列高度。  
  
### <a name="datagrid-row-headers"></a>DataGrid 資料列標頭  
 若要顯示資料列行首<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>屬性必須設為<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>或<xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>。 根據預設，會顯示資料列標頭，並自動調整大小以符合其內容。 在資料列標頭可以根據特定的寬度設定<xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType>屬性。  
  
## <a name="sizing-columns-and-column-headers"></a>調整資料行和資料行標頭  
  
### <a name="datagrid-columns"></a>DataGrid 資料行  
 <xref:System.Windows.Controls.DataGrid>會使用值<xref:System.Windows.Controls.DataGridLength>而<xref:System.Windows.Controls.DataGridLengthUnitType>結構，以指定 絕對 或 自動調整大小模式。  
  
 下表顯示所提供的值<xref:System.Windows.Controls.DataGridLengthUnitType>結構。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|預設的自動調整大小模式大小<xref:System.Windows.Controls.DataGrid>儲存格和資料行標頭的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|儲存格架構自動調整大小模式大小<xref:System.Windows.Controls.DataGrid>中的資料行，不包括資料行行首儲存格的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|行首架構自動調整大小模式大小<xref:System.Windows.Controls.DataGrid>只有資料行行首的內容為基礎的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|以像素為基礎調整大小模式大小<xref:System.Windows.Controls.DataGrid>根據所提供之數值的資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星型的調整大小模式來分配可用空間的加權比例。<br /><br /> 在 XAML，星狀的值會表示為 n * 其中 n 代表一個數字值。 1\*相當於\*。 例如，如果兩個中的資料行<xref:System.Windows.Controls.DataGrid>有的寬度\*和 2 個\*、 第一欄將會收到一個部分的可用空間和第二個資料行就會收到兩個部分的可用空間。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>類別可以用來將數值或字串值之間的資料轉換和<xref:System.Windows.Controls.DataGridLength>值。  
  
 根據預設，<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>屬性設定為<xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>，而<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>屬性設定為<xref:System.Windows.Controls.DataGridLength.Auto%2A>。 當調整大小模式設定為<xref:System.Windows.Controls.DataGridLength.Auto%2A>或<xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>，資料行會成長到其最大的可見內容的寬度。 時向下捲動，這些調整大小模式會導致資料行以展開內容如果大於目前的資料行大小捲動檢視。 之後的內容捲動到檢視之外，都不會壓縮資料行。  
  
 中的資料行<xref:System.Windows.Controls.DataGrid>也可以設定為自動只在指定的界限內的大小或資料行都可以設定特定的大小。 下表顯示可以設定來控制資料行大小的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|設定中的所有資料行的上限<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|設定個別資料行的上限。 覆寫 <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|設定中的所有資料行的下限<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|設定個別資料行的下限。 覆寫 <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|設定中的所有資料行的特定寬度<xref:System.Windows.Controls.DataGrid>。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|設定為指定的寬度，個別資料行。 覆寫 <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>。|  
  
### <a name="datagrid-column-headers"></a>DataGrid 資料行標頭  
 根據預設，<xref:System.Windows.Controls.DataGrid>資料行標頭會顯示。 若要隱藏資料行的標頭<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>屬性必須設為<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>或<xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>。 根據預設，當顯示資料行標頭時，自動調整大小以符合其內容。 資料行標頭可以根據特定的高度設定<xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType>屬性。  
  
### <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 使用者可以調整大小<xref:System.Windows.Controls.DataGrid>資料列和資料行拖曳的資料列或資料行的標頭分隔線。 <xref:System.Windows.Controls.DataGrid>也支援 按兩下資料列或資料行的標題分割線的資料列和資料行自動調整。 若要防止使用者調整特定的資料行大小，將<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>屬性設`false`個別資料行。 若要防止使用者調整所有資料行，將<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>屬性設`false`。 若要防止使用者調整所有資料列，將<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType>屬性設`false`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
