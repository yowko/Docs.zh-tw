---
title: DataGrid 控制項中的調整大小選項
description: 瞭解如何將 Windows Presentation Foundation DataGrid 控制項中的個別資料列和資料行設定為其內容大小或特定值。
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164745"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid 控制項中的調整大小選項
有各種選項可用來控制自己的 <xref:System.Windows.Controls.DataGrid> 大小。 <xref:System.Windows.Controls.DataGrid>、和中的個別資料列和資料行 <xref:System.Windows.Controls.DataGrid> 可以自動設定為其內容，也可以設定為特定值。 根據預設， <xref:System.Windows.Controls.DataGrid> 會擴大和縮小以符合其內容的大小。  
  
## <a name="sizing-the-datagrid"></a>調整 DataGrid 大小  
  
### <a name="cautions-when-using-automatic-sizing"></a>使用自動調整大小時的警告  
 根據預設，的 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性 <xref:System.Windows.Controls.DataGrid> 會設定為 <xref:System.Double.NaN?displayProperty=nameWithType> （ `Auto` XAML 中的 ""），而 <xref:System.Windows.Controls.DataGrid> 會調整為其內容的大小。  
  
 放在不會限制其子系大小的容器內（例如 <xref:System.Windows.Controls.Canvas> 或）時， <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.DataGrid> 將會延伸超過容器的可見界限，而且不會顯示捲軸。 此狀況同時具有可用性和效能含意。  
  
 當系結至資料集時，如果的 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> 不受限制，則會繼續為系結資料集中的每個資料項目加入一個資料列。 這可能會導致在 <xref:System.Windows.Controls.DataGrid> 新增資料列時，在應用程式的可見界限外成長。 <xref:System.Windows.Controls.DataGrid>在此情況下，將不會顯示捲軸，因為它 <xref:System.Windows.FrameworkElement.Height%2A> 會繼續成長以容納新的資料列。  
  
 會針對中的每個資料列建立物件 <xref:System.Windows.Controls.DataGrid> 。 如果您使用的是大型資料集，而且您允許 <xref:System.Windows.Controls.DataGrid> 自動調整其大小，則建立大量物件可能會影響應用程式的效能。  
  
 若要在使用大型資料集時避免這些問題，建議您特別設定的，或將 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> 它放在將會限制其 <xref:System.Windows.FrameworkElement.Height%2A> （例如）的容器中 <xref:System.Windows.Controls.Grid> 。 當受到 <xref:System.Windows.FrameworkElement.Height%2A> 限制時， <xref:System.Windows.Controls.DataGrid> 將只會建立符合其指定範圍的資料列 <xref:System.Windows.FrameworkElement.Height%2A> ，並視需要回收這些資料列以顯示新的資料。  
  
### <a name="setting-the-datagrid-size"></a>設定 DataGrid 大小  
 <xref:System.Windows.Controls.DataGrid>可以設定為在指定的界限內自動調整大小，或 <xref:System.Windows.Controls.DataGrid> 可以設定為特定的大小。 下表顯示可設定以控制大小的屬性 <xref:System.Windows.Controls.DataGrid> 。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|設定的特定高度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|設定的高度上限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>會垂直成長，直到達到此高度為止。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|設定的高度下限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>會垂直縮小，直到達到此高度為止。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|設定的特定寬度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|設定之寬度的上限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>會水準成長，直到達到此寬度為止。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|設定的寬度下限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>會水準縮小，直到達到此寬度為止。|  
  
## <a name="sizing-rows-and-row-headers"></a>調整資料列和資料行標頭的大小  
  
### <a name="datagrid-rows"></a>DataGrid 資料列  
 根據預設，資料 <xref:System.Windows.Controls.DataGrid> 列的 <xref:System.Windows.FrameworkElement.Height%2A> 屬性會設定為 <xref:System.Double.NaN?displayProperty=nameWithType> （ `Auto` XAML 中的 ""），而資料列高度會擴展到其內容的大小。 您 <xref:System.Windows.Controls.DataGrid> 可以藉由設定屬性來指定中所有資料列的高度 <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> 。 使用者可以藉由拖曳資料列行首的分隔線來變更資料列高度。  
  
### <a name="datagrid-row-headers"></a>DataGrid 資料列標頭  
 若要顯示資料列標頭， <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 屬性必須設定為 <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> 。 根據預設，會顯示資料列標題，並自動調整其大小以符合其內容。 藉由設定屬性，可以指定特定寬度的資料列標頭 <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> 。  
  
## <a name="sizing-columns-and-column-headers"></a>調整資料行和資料行標題  
  
### <a name="datagrid-columns"></a>DataGrid 資料行  
 會 <xref:System.Windows.Controls.DataGrid> 使用 <xref:System.Windows.Controls.DataGridLength> 和結構的值 <xref:System.Windows.Controls.DataGridLengthUnitType> 來指定絕對或自動調整大小模式。  
  
 下表顯示結構所提供的值 <xref:System.Windows.Controls.DataGridLengthUnitType> 。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|預設的自動調整大小模式會 <xref:System.Windows.Controls.DataGrid> 根據儲存格和資料行標頭的內容來調整資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|以資料格為基礎的自動調整大小模式會根據資料行中的資料 <xref:System.Windows.Controls.DataGrid> 格內容來調整資料行，而不會包含資料行標頭。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|以標頭為基礎的自動調整大小模式只會根據資料行標 <xref:System.Windows.Controls.DataGrid> 頭的內容來調整資料行的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|以圖元為基礎的調整大小模式會 <xref:System.Windows.Controls.DataGrid> 根據所提供的數值來調整資料行。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星號調整大小模式是用來以加權比例散發可用空間。<br /><br /> 在 XAML 中，星號值是以 n * 表示，其中 n 代表數值。 1 \* 相當於 \* 。 例如，如果中的兩個數據行 <xref:System.Windows.Controls.DataGrid> 寬度為 \* 和 2 \* ，第一個資料行會收到可用空間的其中一個部分，而第二個數據行則會接收兩個可用空間的部分。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>類別可以用來轉換數值或字串值與值之間的資料 <xref:System.Windows.Controls.DataGridLength> 。  
  
 根據預設， <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> 屬性會設定為 <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> ，而 <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> 屬性會設定為 <xref:System.Windows.Controls.DataGridLength.Auto%2A> 。 當調整大小模式設定為 <xref:System.Windows.Controls.DataGridLength.Auto%2A> 或時，資料行會 <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> 成長到其最寬可見內容的寬度。 當滾動時，如果大於目前資料行大小的內容滾動到視野中，這些調整大小模式將會導致資料行展開。 在內容外滾動之後，資料行不會縮小。  
  
 中的資料行 <xref:System.Windows.Controls.DataGrid> 也可以設定為只在指定的界限內自動調整大小，或資料行可以設定為特定的大小。 下表顯示可設定以控制資料行大小的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|設定中所有資料行的上限 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|設定個別資料行的上限。 覆寫 <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|設定中所有資料行的下限 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|設定個別資料行的下限。 覆寫 <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|為中的所有資料行設定特定寬度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|設定個別資料行的特定寬度。 覆寫 <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>。|  
  
### <a name="datagrid-column-headers"></a>DataGrid 資料行標題  
 根據預設， <xref:System.Windows.Controls.DataGrid> 會顯示資料行標頭。 若要隱藏資料行標頭， <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 屬性必須設定為 <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> 。 根據預設，當欄標題顯示時，會自動調整其大小以符合其內容。 藉由設定屬性，可以為資料行標頭提供特定的高度 <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> 。  
  
### <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 使用者可以藉 <xref:System.Windows.Controls.DataGrid> 由拖曳資料列或欄標題分隔線來調整資料列和資料行的大小。 <xref:System.Windows.Controls.DataGrid>也支援在資料列或資料行標頭的分隔線上按兩下，以自動調整資料列與資料行的大小。 若要防止使用者調整特定資料行的大小，請將 <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> 個別資料行的屬性設為 `false` 。 若要防止使用者調整所有資料行的大小，請將 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> 屬性設定為 `false` 。 若要防止使用者調整所有資料列的大小，請將 <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> 屬性設定為 `false` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
