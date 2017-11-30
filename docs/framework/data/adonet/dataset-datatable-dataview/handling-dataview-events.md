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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2abade8bbbf5ab8a9d2cf146271e89703ec34cb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataview-events"></a>處理 DataView 的事件
您可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件，判斷是否已更新檢視。 會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。 **ListChanged**事件也會通知您如果新的排序順序或篩選應用程式而有大幅變更您正在檢視的資料列的清單。  
  
 **ListChanged**事件實作**ListChangedEventHandler**委派的<xref:System.ComponentModel>命名空間和當成輸入<xref:System.ComponentModel.ListChangedEventArgs>物件。 您可以判斷發生何種變更使用<xref:System.ComponentModel.ListChangedType>中的列舉值**ListChangedType**屬性**Newindex**物件。 與加入的變更，刪除或移動資料列，新的索引，加入或移動的資料列的先前刪除的資料列的索引可以存取和使用**Listchangedeventargs**屬性**Newindex**物件。 移動的資料移動的資料列的先前索引可以使用存取**Listchangedeventargs**屬性**Newindex**物件。  
  
 **DataViewManager**也會公開**ListChanged**事件，告知您，如果資料表已經加入或移除，或變更對**關聯**的集合基礎**資料集**。  
  
 下列程式碼範例示範如何將加入**ListChanged**事件處理常式。  
  
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
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
