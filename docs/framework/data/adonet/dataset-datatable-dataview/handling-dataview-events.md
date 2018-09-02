---
title: 處理 DataView 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2f30a578c5233e8b86a165dd220efd45348c5042
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401260"
---
# <a name="handling-dataview-events"></a>處理 DataView 的事件
您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。 會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。 **ListChanged**事件也會通知您如果新的排序順序或篩選的應用程式而有大幅變更您正在檢視的資料列的清單。  
  
 **ListChanged**事件會實作**ListChangedEventHandler**委派<xref:System.ComponentModel>命名空間和做為輸入<xref:System.ComponentModel.ListChangedEventArgs>物件。 您可以使用發生何種變更來判斷<xref:System.ComponentModel.ListChangedType>中的列舉值**Listchangedeventargs**屬性**Newindex**物件。 對於與加入的變更，刪除或移動資料列，新的索引，加入或移動的資料列的先前刪除的資料列的索引可以存取和使用**Listchangedeventargs**屬性**Newindex**物件。 在移動的資料移動的資料列的先前索引可以使用來存取**Listchangedeventargs**屬性**Newindex**物件。  
  
 **DataViewManager**也會公開**ListChanged**事件，告知您，如果資料表已加入或移除，或變更已對**關聯**的集合基礎**資料集**。  
  
 下列程式碼範例示範如何新增**ListChanged**事件處理常式。  
  
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
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
