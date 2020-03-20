---
title: 處理 DataView 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151100"
---
# <a name="handling-dataview-events"></a>處理 DataView 的事件
您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。 會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。 如果由於應用了新的排序次序或篩選器，您正在查看的行清單已發生重大變化，則 **"List更改"** 事件也會通知您。  
  
 **List"更改"** 事件實現<xref:System.ComponentModel>命名空間的<xref:System.ComponentModel.ListChangedEventArgs>**ListChanged 事件處理常式**委託，並將作為輸入物件。 您可以使用<xref:System.ComponentModel.ListChangedType> **ListChangeEventArgs**物件的**ListChangeType**屬性中的枚舉值確定發生了哪些類型的更改。 對於涉及添加、刪除或移動行的更改，可以使用**ListChangesEventArgs**物件的**NewIndex**屬性訪問添加或移動行的新索引和已刪除行的上一個索引。 在移動行的情況下，可以使用**ListChangedEventArgs**物件的**OldIndex**屬性訪問移動行的前一個索引。  
  
 **DataViewManager**還會公開**ListChange**事件，以通知您是否已添加或刪除表，或者對基礎**DataSet**的 **"關係"** 集合進行了更改。  
  
 以下代碼示例演示如何添加**ListChanged**事件處理常式。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
