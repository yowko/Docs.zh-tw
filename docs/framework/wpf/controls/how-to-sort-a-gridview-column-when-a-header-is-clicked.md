---
title: 操作說明：在按一下標頭時排序 GridView 資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], GridView
- controls [WPF], ListView
- ListView controls [WPF], sorting GridView columns
- GridView controls [WPF], ListView control
ms.assetid: 4865d720-d147-40ed-83a7-af7587f8aad8
ms.openlocfilehash: 30bcbd8b7cdd4c184560aaa4a2799137da51fc8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554894"
---
# <a name="how-to-sort-a-gridview-column-when-a-header-is-clicked"></a><span data-ttu-id="6bc62-102">操作說明：在按一下標頭時排序 GridView 資料行</span><span class="sxs-lookup"><span data-stu-id="6bc62-102">How to: Sort a GridView Column When a Header Is Clicked</span></span>
<span data-ttu-id="6bc62-103">這個範例示範如何建立<xref:System.Windows.Controls.ListView>實作控制項<xref:System.Windows.Controls.GridView>檢視模式和資料內容，當使用者按一下資料行標頭來排序。</span><span class="sxs-lookup"><span data-stu-id="6bc62-103">This example shows how to create a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView> view mode and sorts the data content when a user clicks a column header.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc62-104">範例</span><span class="sxs-lookup"><span data-stu-id="6bc62-104">Example</span></span>  
 <span data-ttu-id="6bc62-105">下列範例會定義<xref:System.Windows.Controls.GridView>具有三個資料行繫結至<xref:System.DateTime.Year%2A>， <xref:System.DateTime.Month%2A>，和<xref:System.DateTime.Day%2A>，屬性<xref:System.DateTime>結構。</span><span class="sxs-lookup"><span data-stu-id="6bc62-105">The following example defines a <xref:System.Windows.Controls.GridView> with three columns that bind to the <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>, properties of the <xref:System.DateTime> structure.</span></span>  
  
```xaml  
<GridView>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Year}"   
                  Header="Year"  
                  Width="100"/>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Month}"   
                  Header="Month"  
                  Width="100"/>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Day}"   
                  Header="Day"  
                  Width="100"/>  
</GridView>  
```  
  
 <span data-ttu-id="6bc62-106">下列範例顯示定義為資料項目<xref:System.Collections.ArrayList>的<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="6bc62-106">The following example shows the data items that are defined as an <xref:System.Collections.ArrayList> of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="6bc62-107"><xref:System.Collections.ArrayList>定義為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="6bc62-107">The <xref:System.Collections.ArrayList> is defined as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
```xaml  
<ListView.ItemsSource>  
  <s:ArrayList>  
    <p:DateTime>1993/1/1 12:22:02</p:DateTime>  
    <p:DateTime>1993/1/2 13:2:01</p:DateTime>  
    <p:DateTime>1997/1/3 2:1:6</p:DateTime>  
    <p:DateTime>1997/1/4 13:6:55</p:DateTime>  
    <p:DateTime>1999/2/1 12:22:02</p:DateTime>  
    <p:DateTime>1998/2/2 13:2:01</p:DateTime>  
    <p:DateTime>2000/2/3 2:1:6</p:DateTime>  
    <p:DateTime>2002/2/4 13:6:55</p:DateTime>  
    <p:DateTime>2001/3/1 12:22:02</p:DateTime>  
    <p:DateTime>2006/3/2 13:2:01</p:DateTime>  
    <p:DateTime>2004/3/3 2:1:6</p:DateTime>  
    <p:DateTime>2004/3/4 13:6:55</p:DateTime>  
  </s:ArrayList>  
</ListView.ItemsSource>  
```  
  
 <span data-ttu-id="6bc62-108">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中的 `s` 和 `p` 識別碼會參考 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面之中繼資料中定義的命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="6bc62-108">The `s` and `p` identifiers in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tags refer to namespace mappings that are defined in the metadata of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="6bc62-109">下列範例示範中繼資料定義。</span><span class="sxs-lookup"><span data-stu-id="6bc62-109">The following example shows the metadata definition.</span></span>  
  
```xaml  
<Window        
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="ListViewSort.Window1"      
    xmlns:s="clr-namespace:System.Collections;assembly=mscorlib"  
    xmlns:p="clr-namespace:System;assembly=mscorlib">  
```  
  
 <span data-ttu-id="6bc62-110">若要排序的資料，根據資料行的內容，此範例會定義事件處理常式來處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>按資料行的標頭按鈕時所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="6bc62-110">To sort the data according to the contents of a column, the example defines an event handler to handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event that occurs when you press the column header button.</span></span> <span data-ttu-id="6bc62-111">下列範例示範如何指定的事件處理常式<xref:System.Windows.Controls.GridViewColumnHeader>控制項。</span><span class="sxs-lookup"><span data-stu-id="6bc62-111">The following example shows how to specify an event handler for the <xref:System.Windows.Controls.GridViewColumnHeader> control.</span></span>  
  
```xaml  
<ListView x:Name='lv' Height="150" HorizontalAlignment="Center"   
  VerticalAlignment="Center"   
  GridViewColumnHeader.Click="GridViewColumnHeaderClickedHandler"  
 >  
```  
  
 <span data-ttu-id="6bc62-112">此範例會定義事件處理常式，讓排序方向在每次您按下資料行標頭按鈕時，在遞增順序與遞減順序之間做變更。</span><span class="sxs-lookup"><span data-stu-id="6bc62-112">The example defines the event handler so that the sort direction changes between ascending order and descending order each time you press the column header button.</span></span> <span data-ttu-id="6bc62-113">下列範例示範事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6bc62-113">The following example shows the event handler.</span></span>  
  
```csharp  
public partial class Window1 : Window  
{  
    public Window1()  
    {  
        InitializeComponent();  
    }  
  
    GridViewColumnHeader _lastHeaderClicked = null;  
    ListSortDirection _lastDirection = ListSortDirection.Ascending;  
  
    void GridViewColumnHeaderClickedHandler(object sender,  
                                            RoutedEventArgs e)  
    {  
        var headerClicked = e.OriginalSource as GridViewColumnHeader;  
        ListSortDirection direction;  
  
        if (headerClicked != null)  
        {  
            if (headerClicked.Role != GridViewColumnHeaderRole.Padding)  
            {  
                if (headerClicked != _lastHeaderClicked)  
                {  
                    direction = ListSortDirection.Ascending;  
                }  
                else  
                {  
                    if (_lastDirection == ListSortDirection.Ascending)  
                    {  
                        direction = ListSortDirection.Descending;  
                    }  
                    else  
                    {  
                        direction = ListSortDirection.Ascending;  
                    }  
                }  
  
                var columnBinding = headerClicked.Column.DisplayMemberBinding as Binding;
                var sortBy = columnBinding?.Path.Path ?? headerClicked.Column.Header as string;

                Sort(sortBy, direction);
  
                if (direction == ListSortDirection.Ascending)  
                {  
                    headerClicked.Column.HeaderTemplate =  
                      Resources["HeaderTemplateArrowUp"] as DataTemplate;  
                }  
                else  
                {  
                    headerClicked.Column.HeaderTemplate =  
                      Resources["HeaderTemplateArrowDown"] as DataTemplate;  
                }  
  
                // Remove arrow from previously sorted header  
                if (_lastHeaderClicked != null && _lastHeaderClicked != headerClicked)  
                {  
                    _lastHeaderClicked.Column.HeaderTemplate = null;  
                }  
  
                _lastHeaderClicked = headerClicked;  
                _lastDirection = direction;  
            }  
        }  
    }
}
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window
    Public Sub New()  
        InitializeComponent()  
    End Sub  
  
    Private _lastHeaderClicked As GridViewColumnHeader = Nothing  
    Private _lastDirection As ListSortDirection = ListSortDirection.Ascending  
  
    Private Sub GridViewColumnHeaderClickedHandler(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        Dim headerClicked = TryCast(e.OriginalSource, GridViewColumnHeader)  
        Dim direction As ListSortDirection  
  
        If headerClicked IsNot Nothing Then  
            If headerClicked.Role <> GridViewColumnHeaderRole.Padding Then  
                If headerClicked IsNot _lastHeaderClicked Then  
                    direction = ListSortDirection.Ascending  
                Else  
                    If _lastDirection = ListSortDirection.Ascending Then  
                        direction = ListSortDirection.Descending  
                    Else  
                        direction = ListSortDirection.Ascending  
                    End If  
                End If  

                Dim columnBinding = TryCast(headerClicked.Column.DisplayMemberBinding, Binding)
                Dim sortBy = If(columnBinding?.Path.Path, TryCast(headerClicked.Column.Header, String))

                Sort(sortBy, direction)  

                If direction = ListSortDirection.Ascending Then
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowUp"), DataTemplate)  
                Else  
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowDown"), DataTemplate)  
                End If  
  
                ' Remove arrow from previously sorted header  
                If _lastHeaderClicked IsNot Nothing AndAlso _lastHeaderClicked IsNot headerClicked Then  
                    _lastHeaderClicked.Column.HeaderTemplate = Nothing  
                End If  
  
                _lastHeaderClicked = headerClicked  
                _lastDirection = direction  
            End If  
        End If  
    End Sub
End Class
```  
  
 <span data-ttu-id="6bc62-114">下列範例示範事件處理常式所呼叫來排序資料的排序演算法。</span><span class="sxs-lookup"><span data-stu-id="6bc62-114">The following example shows the sorting algorithm that is called by the event handler to sort the data.</span></span> <span data-ttu-id="6bc62-115">藉由建立新的執行排序<xref:System.ComponentModel.SortDescription>結構。</span><span class="sxs-lookup"><span data-stu-id="6bc62-115">The sort is performed by creating a new <xref:System.ComponentModel.SortDescription> structure.</span></span>  
  
```csharp  
private void Sort(string sortBy, ListSortDirection direction)  
{  
    ICollectionView dataView =  
      CollectionViewSource.GetDefaultView(lv.ItemsSource);  
  
    dataView.SortDescriptions.Clear();  
    SortDescription sd = new SortDescription(sortBy, direction);  
    dataView.SortDescriptions.Add(sd);  
    dataView.Refresh();  
}  
```  
  
```vb  
Private Sub Sort(ByVal sortBy As String, ByVal direction As ListSortDirection)  
    Dim dataView As ICollectionView = CollectionViewSource.GetDefaultView(lv.ItemsSource)  
  
    dataView.SortDescriptions.Clear()  
    Dim sd As New SortDescription(sortBy, direction)  
    dataView.SortDescriptions.Add(sd)  
    dataView.Refresh()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bc62-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc62-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="6bc62-117">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="6bc62-117">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="6bc62-118">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="6bc62-118">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="6bc62-119">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="6bc62-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
