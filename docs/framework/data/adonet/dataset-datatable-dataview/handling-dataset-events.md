---
title: "處理 DataSet 的事件"
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
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 820d93529fc12f3eeacd730cc66ec85ffd560ff9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="handling-dataset-events"></a><span data-ttu-id="9af2a-102">處理 DataSet 的事件</span><span class="sxs-lookup"><span data-stu-id="9af2a-102">Handling DataSet Events</span></span>
<span data-ttu-id="9af2a-103"><xref:System.Data.DataSet> 物件提供三個事件： <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>和 <xref:System.Data.DataSet.MergeFailed>。</span><span class="sxs-lookup"><span data-stu-id="9af2a-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="9af2a-104">MergeFailed 事件</span><span class="sxs-lookup"><span data-stu-id="9af2a-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="9af2a-105">`DataSet` 物件最常用的事件為 `MergeFailed`，此事件會在正在合併之 `DataSet` 物件的結構描述發生衝突時引發。</span><span class="sxs-lookup"><span data-stu-id="9af2a-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="9af2a-106">當目標與來源 <xref:System.Data.DataRow> 具有相同的主索引鍵值，且 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設為 `true`時，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="9af2a-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="9af2a-107">例如，如果進行合併之資料表中的主索引鍵資料行與兩個 `DataSet` 物件中的資料表相同，便會擲回例外狀況且引發 `MergeFailed` 事件。</span><span class="sxs-lookup"><span data-stu-id="9af2a-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="9af2a-108">傳遞給 <xref:System.Data.MergeFailedEventArgs> 事件的 `MergeFailed` 物件具有 <xref:System.Data.MergeFailedEventArgs.Conflict%2A> 屬性，可識別兩個 `DataSet` 物件間的結構描述衝突，也具有 <xref:System.Data.MergeFailedEventArgs.Table%2A> 屬性，可識別發生衝突的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9af2a-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="9af2a-109">下列程式碼片段會顯示如何加入 `MergeFailed` 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9af2a-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="9af2a-110">初始化的事件</span><span class="sxs-lookup"><span data-stu-id="9af2a-110">The Initialized Event</span></span>  
 <span data-ttu-id="9af2a-111"><xref:System.Data.DataSet.Initialized> 事件發生在 `DataSet` 建構函式 (Constructor) 初始化 `DataSet`的新執行個體 (Instance) 之後。</span><span class="sxs-lookup"><span data-stu-id="9af2a-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="9af2a-112">如果 <xref:System.Data.DataSet.IsInitialized%2A> 已完成初始化， `true` 屬性會傳回 `DataSet` ，否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="9af2a-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="9af2a-113">開始 <xref:System.Data.DataSet.BeginInit%2A> 初始化作業的 `DataSet`方法會將 <xref:System.Data.DataSet.IsInitialized%2A> 設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9af2a-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="9af2a-114"><xref:System.Data.DataSet.EndInit%2A> 方法 (結束 `DataSet`的初始化) 會將其設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9af2a-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="9af2a-115">[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 設計環境會使用這些方法初始化其他元件正在使用的 `DataSet` 。</span><span class="sxs-lookup"><span data-stu-id="9af2a-115">These methods are used by the [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="9af2a-116">您通常不會在程式碼中使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="9af2a-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="9af2a-117">已處置的事件</span><span class="sxs-lookup"><span data-stu-id="9af2a-117">The Disposed Event</span></span>  
 <span data-ttu-id="9af2a-118">`DataSet` 是衍生自 <xref:System.ComponentModel.MarshalByValueComponent> 類別 (Class)，此類別會公開 (Expose) <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 方法和 <xref:System.ComponentModel.MarshalByValueComponent.Disposed> 事件。</span><span class="sxs-lookup"><span data-stu-id="9af2a-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="9af2a-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件加入事件處理常式來接聽元件上清除的事件。</span><span class="sxs-lookup"><span data-stu-id="9af2a-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="9af2a-120">您可以使用<xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件`DataSet`如果您想要執行程式碼時<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9af2a-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="9af2a-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>所使用的資源釋出<xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="9af2a-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9af2a-122">`DataSet`和`DataTable`物件繼承自<xref:System.ComponentModel.MarshalByValueComponent>和支援<xref:System.Runtime.Serialization.ISerializable>遠端執行功能的介面。</span><span class="sxs-lookup"><span data-stu-id="9af2a-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="9af2a-123">這些是唯一可以進行遠端通訊的 ADO.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="9af2a-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="9af2a-124">如需詳細資訊，請參閱[遠端物件](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)。</span><span class="sxs-lookup"><span data-stu-id="9af2a-124">For more information, see [Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="9af2a-125">如需有關使用時可使用其他事件資訊`DataSet`，請參閱[處理 DataTable 的事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)和[處理 DataAdapter 事件](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="9af2a-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af2a-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="9af2a-126">See Also</span></span>  
 [<span data-ttu-id="9af2a-127">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="9af2a-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9af2a-128">驗證資料</span><span class="sxs-lookup"><span data-stu-id="9af2a-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="9af2a-129">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="9af2a-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="9af2a-130">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="9af2a-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
