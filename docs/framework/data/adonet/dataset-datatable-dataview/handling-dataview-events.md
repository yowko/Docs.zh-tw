---
title: "處理 DataView 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 處理 DataView 事件
您可以使用 <xref:System.Data.DataView> 的 <xref:System.Data.DataView.ListChanged> 事件，判斷是否已更新檢視。  會引發事件的更新包括：加入、刪除或修改基底資料表中的資料列、在基底資料表的結構描述中加入或刪除資料行，以及在父關聯性或子關聯性中進行變更。  若您正在檢視的資料列清單因套用了新的排序順序或篩選而有大幅變更，**ListChanged** 事件也會告知您。  
  
 **ListChanged** 事件會實作 <xref:System.ComponentModel> 命名空間的 **ListChangedEventHandler** 委派，並將 <xref:System.ComponentModel.ListChangedEventArgs> 物件做為輸入。  您可以使用 **ListChangedEventArgs** 物件之 **ListChangedType** 屬性中的 <xref:System.ComponentModel.ListChangedType> 列舉值來判斷發生的變更類型。  對於與加入、刪除或移動資料列相關的變更，您可以使用 **ListChangedEventArgs** 物件的 **NewIndex** 屬性，存取已加入或移動之資料列的新索引，和已刪除之資料列先前的索引。  以移動的資料列為例，您可以透過 **ListChangedEventArgs** 物件的 **OldIndex** 屬性來存取移動的資料列的先前索引。  
  
 **DataViewManager** 也會公開 **ListChanged** 事件，告知您資料表是否已經加入或移除，或者基礎 **DataSet** 的 **Relations** 集合是否已經發生變更。  
  
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
  
## 請參閱  
 <xref:System.Data.DataView>   
 <xref:System.ComponentModel.ListChangedEventHandler>   
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)