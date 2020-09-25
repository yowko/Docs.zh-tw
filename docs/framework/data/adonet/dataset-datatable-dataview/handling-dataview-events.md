---
title: 處理 DataView 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2a67cb040c5d438d17ad91d41e97f24f3166262b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204537"
---
# <a name="handling-dataview-events"></a>處理 DataView 的事件

您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。 會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。 **ListChanged**事件也會在您要查看的資料列清單因為應用新的排序次序或篩選而大幅變更時通知您。  
  
 **ListChanged**事件會執行命名空間的**ListChangedEventHandler**委派 <xref:System.ComponentModel> ，並將物件做為輸入 <xref:System.ComponentModel.ListChangedEventArgs> 。 您可以使用 <xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs**物件之**system.componentmodel.listchangedtype>** 屬性中的列舉值，判斷發生了何種類型的變更。 對於涉及新增、刪除或移動資料列的變更，您可以使用**ListChangedEventArgs**物件的**NewIndex**屬性來存取加入或移動之資料列的新索引，以及已刪除資料列的先前索引。 在移動的資料列案例中，可以使用**ListChangedEventArgs**物件的**OldIndex**屬性來存取移動之資料列的先前索引。  
  
 **DataViewManager**也會公開**ListChanged**事件，以通知您是否已加入或移除資料表，或者是否已對基礎**資料集**的**關聯集合進行**變更。  
  
 下列程式碼範例顯示如何加入 **ListChanged** 事件處理常式。  
  
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
