---
title: 處理 DataSet 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: b2b71dac58838a826933af570934bf4bbb35e025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784603"
---
# <a name="handling-dataset-events"></a>處理 DataSet 的事件
<xref:System.Data.DataSet> 物件提供三個事件： <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>和 <xref:System.Data.DataSet.MergeFailed>。  
  
## <a name="the-mergefailed-event"></a>MergeFailed 事件  
 `DataSet` 物件最常用的事件為 `MergeFailed`，此事件會在正在合併之 `DataSet` 物件的結構描述發生衝突時引發。 當目標與來源 <xref:System.Data.DataRow> 具有相同的主索引鍵值，且 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設為 `true`時，就會發生此情況。 例如，如果進行合併之資料表中的主索引鍵資料行與兩個 `DataSet` 物件中的資料表相同，便會擲回例外狀況且引發 `MergeFailed` 事件。 傳遞給 <xref:System.Data.MergeFailedEventArgs> 事件的 `MergeFailed` 物件具有 <xref:System.Data.MergeFailedEventArgs.Conflict%2A> 屬性，可識別兩個 `DataSet` 物件間的結構描述衝突，也具有 <xref:System.Data.MergeFailedEventArgs.Table%2A> 屬性，可識別發生衝突的資料表名稱。  
  
 下列程式碼片段會顯示如何加入 `MergeFailed` 事件的事件處理常式。  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>初始化的事件  
 <xref:System.Data.DataSet.Initialized> 事件發生在 `DataSet` 建構函式 (Constructor) 初始化 `DataSet`的新執行個體 (Instance) 之後。  
  
 如果 <xref:System.Data.DataSet.IsInitialized%2A> 已完成初始化， `true` 屬性會傳回 `DataSet` ，否則會傳回 `false`。 開始 <xref:System.Data.DataSet.BeginInit%2A> 初始化作業的 `DataSet`方法會將 <xref:System.Data.DataSet.IsInitialized%2A> 設為 `false`。 <xref:System.Data.DataSet.EndInit%2A> 方法 (結束 `DataSet`的初始化) 會將其設定為 `true`。 Visual Studio 設計環境會使用這些方法來初始化`DataSet`另一個元件所使用的。 您通常不會在程式碼中使用這些方法。  
  
## <a name="the-disposed-event"></a>已處置的事件  
 `DataSet` 是衍生自 <xref:System.ComponentModel.MarshalByValueComponent> 類別 (Class)，此類別會公開 (Expose) <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 方法和 <xref:System.ComponentModel.MarshalByValueComponent.Disposed> 事件。 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件會新增事件處理常式，以接聽元件上的已處置事件。 `DataSet`如果您想要在<xref:System.ComponentModel.MarshalByValueComponent.Disposed>呼叫方法時執行程式碼，可以<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>使用的事件。 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>釋放所<xref:System.ComponentModel.MarshalByValueComponent>使用的資源。  
  
> [!NOTE]
> 和物件繼承自<xref:System.ComponentModel.MarshalByValueComponent> ，並且支援遠端的介面。<xref:System.Runtime.Serialization.ISerializable> `DataTable` `DataSet` 這些是唯一可以進行遠端通訊的 ADO.NET 物件。 如需詳細資訊，請參閱[.Net 遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))。  
  
 如需使用`DataSet`時其他可用事件的詳細資訊，請參閱[處理 DataTable 事件](handling-datatable-events.md)和[處理 DataAdapter 事件](../handling-dataadapter-events.md)。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [驗證資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120)) \(機器翻譯\)
- [在 ADO.NET 中擷取和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
