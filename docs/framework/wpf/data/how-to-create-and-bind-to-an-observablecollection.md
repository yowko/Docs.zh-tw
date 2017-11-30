---
title: "操作說明：建立和繫結至 ObservableCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7918d97f2f1bcd521e7e7e38231c999d2fbda53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a><span data-ttu-id="03928-102">操作說明：建立和繫結至 ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="03928-102">How to: Create and Bind to an ObservableCollection</span></span>
<span data-ttu-id="03928-103">此範例示範如何建立並繫結至集合，其中衍生自<xref:System.Collections.ObjectModel.ObservableCollection%601>類別，即會加入或移除項目時提供通知的集合類別。</span><span class="sxs-lookup"><span data-stu-id="03928-103">This example shows how to create and bind to a collection that derives from the <xref:System.Collections.ObjectModel.ObservableCollection%601> class, which is a collection class that provides notifications when items get added or removed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03928-104">範例</span><span class="sxs-lookup"><span data-stu-id="03928-104">Example</span></span>  
 <span data-ttu-id="03928-105">下列範例顯示 `NameList` 集合的實作：</span><span class="sxs-lookup"><span data-stu-id="03928-105">The following example shows the implementation of a `NameList` collection:</span></span>  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 <span data-ttu-id="03928-106">您可以使用讓其他[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件變為可用的相同方式，將集合變為可用來進行繫結 (如[讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)中所述)。</span><span class="sxs-lookup"><span data-stu-id="03928-106">You can make the collection available for binding the same way you would with other [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects, as described in [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span> <span data-ttu-id="03928-107">例如，您可以使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 具現化集合，並將集合指定為資源 (如這裡所示)：</span><span class="sxs-lookup"><span data-stu-id="03928-107">For example, you can instantiate the collection in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and specify the collection as a resource, as shown here:</span></span>  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 <span data-ttu-id="03928-108">然後，就可以繫結至集合：</span><span class="sxs-lookup"><span data-stu-id="03928-108">You can then bind to the collection:</span></span>  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 <span data-ttu-id="03928-109">這裡並未顯示 `NameItemTemplate` 的定義。</span><span class="sxs-lookup"><span data-stu-id="03928-109">The definition of `NameItemTemplate` is not shown here.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03928-110">集合中的物件必須滿足[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)中所述的需求。</span><span class="sxs-lookup"><span data-stu-id="03928-110">The objects in your collection must satisfy the requirements described in the [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span> <span data-ttu-id="03928-111">特別是，如果您使用<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>(例如，您想您[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]時動態變更的來源屬性更新)，您必須實作適當的屬性已變更通知機制，例如<xref:System.ComponentModel.INotifyPropertyChanged>介面。</span><span class="sxs-lookup"><span data-stu-id="03928-111">In particular, if you are using <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> (for example, you want your [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to update when the source properties change dynamically), you must implement a suitable property changed notification mechanism such as the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span>  
  
 <span data-ttu-id="03928-112">如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)中的＜繫結至集合＞一節。</span><span class="sxs-lookup"><span data-stu-id="03928-112">For more information, see the Binding to Collections section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03928-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03928-113">See Also</span></span>  
 [<span data-ttu-id="03928-114">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="03928-114">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="03928-115">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="03928-115">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="03928-116">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="03928-116">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="03928-117">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="03928-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="03928-118">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="03928-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
