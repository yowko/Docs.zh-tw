---
title: "處理 DataView 的事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf3b02227de5068a031cedb73269148c7d5262a0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataview-events"></a><span data-ttu-id="83618-102">處理 DataView 的事件</span><span class="sxs-lookup"><span data-stu-id="83618-102">Handling DataView Events</span></span>
<span data-ttu-id="83618-103">您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。</span><span class="sxs-lookup"><span data-stu-id="83618-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="83618-104">會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。</span><span class="sxs-lookup"><span data-stu-id="83618-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="83618-105">**ListChanged**事件也會通知您如果新的排序順序或篩選應用程式而有大幅變更您正在檢視的資料列的清單。</span><span class="sxs-lookup"><span data-stu-id="83618-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="83618-106">**ListChanged**事件實作**ListChangedEventHandler**委派的<xref:System.ComponentModel>命名空間和當成輸入<xref:System.ComponentModel.ListChangedEventArgs>物件。</span><span class="sxs-lookup"><span data-stu-id="83618-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="83618-107">您可以判斷發生何種變更使用<xref:System.ComponentModel.ListChangedType>中的列舉值**ListChangedType**屬性**Newindex**物件。</span><span class="sxs-lookup"><span data-stu-id="83618-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="83618-108">與加入的變更，刪除或移動資料列，新的索引，加入或移動的資料列的先前刪除的資料列的索引可以存取和使用**Listchangedeventargs**屬性**Newindex**物件。</span><span class="sxs-lookup"><span data-stu-id="83618-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="83618-109">移動的資料移動的資料列的先前索引可以使用存取**Listchangedeventargs**屬性**Newindex**物件。</span><span class="sxs-lookup"><span data-stu-id="83618-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="83618-110">**DataViewManager**也會公開**ListChanged**事件，告知您，如果資料表已經加入或移除，或變更對**關聯**的集合基礎**資料集**。</span><span class="sxs-lookup"><span data-stu-id="83618-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="83618-111">下列程式碼範例示範如何將加入**ListChanged**事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="83618-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83618-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="83618-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="83618-113">DataView</span><span class="sxs-lookup"><span data-stu-id="83618-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="83618-114">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="83618-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
