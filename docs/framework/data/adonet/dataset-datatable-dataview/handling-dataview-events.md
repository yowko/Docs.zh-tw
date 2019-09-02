---
title: 處理 DataView 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b3a1077bff9bf457b4aef0b05357d4a9260f8973
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204817"
---
# <a name="handling-dataview-events"></a>處理 DataView 的事件
您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。 會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。 如果您要查看的資料列清單因為應用新的排序次序或篩選而大幅變更, **ListChanged**事件也會通知您。  
  
 **ListChanged**事件會實作為 <xref:System.ComponentModel> <xref:System.ComponentModel.ListChangedEventArgs>命名空間的 ListChangedEventHandler 委派, 並接受物件的輸入。 您可以使用<xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs**物件的**system.componentmodel.listchangedtype>** 屬性中的列舉值, 判斷已發生的變更類型。 對於涉及加入、刪除或移動資料列的變更, 您可以使用**ListChangedEventArgs**物件的**NewIndex**屬性來存取已加入或移動之資料列的新索引, 以及已刪除之資料列的先前索引。 在移動的資料列案例中, 您可以使用**ListChangedEventArgs**物件的**OldIndex**屬性來存取已移動之資料列的先前索引。  
  
 **DataViewManager**也會公開**ListChanged**事件, 以在資料表已加入或移除, 或者基礎**資料集**的關聯集合已進行變更時通知您 。  
  
 下列程式碼範例顯示如何加入**ListChanged**事件處理常式。  
  
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
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
