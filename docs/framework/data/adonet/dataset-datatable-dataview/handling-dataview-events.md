---
title: 處理 DataView 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784595"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="a9e05-102">處理 DataView 的事件</span><span class="sxs-lookup"><span data-stu-id="a9e05-102">Handling DataView Events</span></span>
<span data-ttu-id="a9e05-103">您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。</span><span class="sxs-lookup"><span data-stu-id="a9e05-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="a9e05-104">會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。</span><span class="sxs-lookup"><span data-stu-id="a9e05-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="a9e05-105">如果您要查看的資料列清單因為應用新的排序次序或篩選而大幅變更， **ListChanged**事件也會通知您。</span><span class="sxs-lookup"><span data-stu-id="a9e05-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="a9e05-106">**ListChanged**事件會實作為 <xref:System.ComponentModel> <xref:System.ComponentModel.ListChangedEventArgs>命名空間的 ListChangedEventHandler 委派，並接受物件的輸入。</span><span class="sxs-lookup"><span data-stu-id="a9e05-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="a9e05-107">您可以使用<xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs**物件的**system.componentmodel.listchangedtype>** 屬性中的列舉值，判斷已發生的變更類型。</span><span class="sxs-lookup"><span data-stu-id="a9e05-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="a9e05-108">對於涉及加入、刪除或移動資料列的變更，您可以使用**ListChangedEventArgs**物件的**NewIndex**屬性來存取已加入或移動之資料列的新索引，以及已刪除之資料列的先前索引。</span><span class="sxs-lookup"><span data-stu-id="a9e05-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="a9e05-109">在移動的資料列案例中，您可以使用**ListChangedEventArgs**物件的**OldIndex**屬性來存取已移動之資料列的先前索引。</span><span class="sxs-lookup"><span data-stu-id="a9e05-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="a9e05-110">**DataViewManager**也會公開**ListChanged**事件，以在資料表已加入或移除，或者基礎**資料集**的**關聯集合已**進行變更時通知您。</span><span class="sxs-lookup"><span data-stu-id="a9e05-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="a9e05-111">下列程式碼範例顯示如何加入**ListChanged**事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a9e05-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9e05-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9e05-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="a9e05-113">DataView</span><span class="sxs-lookup"><span data-stu-id="a9e05-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="a9e05-114">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="a9e05-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
