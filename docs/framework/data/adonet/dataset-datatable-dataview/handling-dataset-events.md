---
title: 處理 DataSet 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: ff684adcb4e23b91b3e59476299d277c90c22c51
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857767"
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
  
 如果 <xref:System.Data.DataSet.IsInitialized%2A> 已完成初始化， `true` 屬性會傳回 `DataSet` ，否則會傳回 `false`。 開始 <xref:System.Data.DataSet.BeginInit%2A> 初始化作業的 `DataSet`方法會將 <xref:System.Data.DataSet.IsInitialized%2A> 設為 `false`。 <xref:System.Data.DataSet.EndInit%2A> 方法 (結束 `DataSet`的初始化) 會將其設定為 `true`。 在 Visual Studio 設計環境會用這些方法來初始化`DataSet`，正由另一個元件。 您通常不會在程式碼中使用這些方法。  
  
## <a name="the-disposed-event"></a>已處置的事件  
 `DataSet` 是衍生自 <xref:System.ComponentModel.MarshalByValueComponent> 類別 (Class)，此類別會公開 (Expose) <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 方法和 <xref:System.ComponentModel.MarshalByValueComponent.Disposed> 事件。 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件加入事件處理常式來接聽元件上清除的事件。 您可以使用<xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件的`DataSet`如果您想要執行程式碼時<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>呼叫方法。 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 釋放所使用的資源<xref:System.ComponentModel.MarshalByValueComponent>。  
  
> [!NOTE]
>  `DataSet`並`DataTable`物件會繼承自<xref:System.ComponentModel.MarshalByValueComponent>且支援<xref:System.Runtime.Serialization.ISerializable>針對遠端執行功能的介面。 這些是唯一可以進行遠端通訊的 ADO.NET 物件。 如需詳細資訊，請參閱 <<c0> [ 遠端物件](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)。  
  
 如需可用時使用的其他事件資訊`DataSet`，請參閱[DataTable 事件處理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)並[處理 DataAdapter 事件](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
## <a name="see-also"></a>另請參閱  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [驗證資料](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [在 ADO.NET 中擷取和修改資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
