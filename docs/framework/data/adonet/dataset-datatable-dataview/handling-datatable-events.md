---
title: "處理 DataTable 的事件"
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
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7ab9d1043fdd1d4d78ec09390f227f297e471c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="handling-datatable-events"></a><span data-ttu-id="ec5e8-102">處理 DataTable 的事件</span><span class="sxs-lookup"><span data-stu-id="ec5e8-102">Handling DataTable Events</span></span>
<span data-ttu-id="ec5e8-103"><xref:System.Data.DataTable> 物件提供一系列可由應用程式處理的事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-103">The <xref:System.Data.DataTable> object provides a series of events that can be processed by an application.</span></span> <span data-ttu-id="ec5e8-104">下表說明 `DataTable` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-104">The following table describes `DataTable` events.</span></span>  
  
|<span data-ttu-id="ec5e8-105">事件</span><span class="sxs-lookup"><span data-stu-id="ec5e8-105">Event</span></span>|<span data-ttu-id="ec5e8-106">描述</span><span class="sxs-lookup"><span data-stu-id="ec5e8-106">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|<span data-ttu-id="ec5e8-107">發生在呼叫 <xref:System.Data.DataTable.EndInit%2A> 的 `DataTable` 方法之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-107">Occurs after the <xref:System.Data.DataTable.EndInit%2A> method of a `DataTable` is called.</span></span> <span data-ttu-id="ec5e8-108">這個事件主要是為了支援設計階段案例而提供。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-108">This event is intended primarily to support design-time scenarios.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanged>|<span data-ttu-id="ec5e8-109">發生在成功變更 <xref:System.Data.DataColumn> 中的值之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-109">Occurs after a value has been successfully changed in a <xref:System.Data.DataColumn>.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanging>|<span data-ttu-id="ec5e8-110">發生在 `DataColumn` 的值送出之時。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-110">Occurs when a value has been submitted for a `DataColumn`.</span></span>|  
|<xref:System.Data.DataTable.RowChanged>|<span data-ttu-id="ec5e8-111">發生在 `DataColumn` 中的 <xref:System.Data.DataRow.RowState%2A> 值或 <xref:System.Data.DataRow> 的 `DataTable` 成功變更之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-111">Occurs after a `DataColumn` value or the <xref:System.Data.DataRow.RowState%2A> of a <xref:System.Data.DataRow> in the `DataTable` has been changed successfully.</span></span>|  
|<xref:System.Data.DataTable.RowChanging>|<span data-ttu-id="ec5e8-112">發生在 `DataColumn` 中的 `RowState` 值或`DataRow` 的 `DataTable` 變更送出之時。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-112">Occurs when a change has been submitted for a `DataColumn` value or the `RowState` of a `DataRow` in the `DataTable`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleted>|<span data-ttu-id="ec5e8-113">發生在 `DataRow` 中的 `DataTable` 標記為 `Deleted` 之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-113">Occurs after a `DataRow` in the `DataTable` has been marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleting>|<span data-ttu-id="ec5e8-114">發生在 `DataRow` 中的 `DataTable` 標記為 `Deleted` 之前。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-114">Occurs before a `DataRow` in the `DataTable` is marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.TableCleared>|<span data-ttu-id="ec5e8-115">發生在 <xref:System.Data.DataTable.Clear%2A> 的 `DataTable` 方法成功清除每個 `DataRow` 之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-115">Occurs after a call to the <xref:System.Data.DataTable.Clear%2A> method of the `DataTable` has successfully cleared every `DataRow`.</span></span>|  
|<xref:System.Data.DataTable.TableClearing>|<span data-ttu-id="ec5e8-116">發生在呼叫 `Clear` 方法之後，但在 `Clear` 作業開始之前。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-116">Occurs after the `Clear` method is called but before the `Clear` operation begins.</span></span>|  
|<xref:System.Data.DataTable.TableNewRow>|<span data-ttu-id="ec5e8-117">發生在藉由呼叫 `DataRow` 的 `NewRow` 方法而建立新的 `DataTable` 之後。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-117">Occurs after a new `DataRow` is created by a call to the `NewRow` method of the `DataTable`.</span></span>|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|<span data-ttu-id="ec5e8-118">發生在 `DataTable` 為 `Disposed` 時。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-118">Occurs when the `DataTable` is `Disposed`.</span></span> <span data-ttu-id="ec5e8-119">繼承自 <xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-119">Inherited from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ec5e8-120">大多數加入或刪除資料列的作業都不會引發 `ColumnChanged` 和 `ColumnChanging` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-120">Most operations that add or delete rows do not raise the `ColumnChanged` and `ColumnChanging` events.</span></span> <span data-ttu-id="ec5e8-121">不過，`ReadXml` 方法不會引發 `ColumnChanged` 和 `ColumnChanging` 事件，除非正在讀取的 XML 文件是 `XmlReadMode`，而 `DiffGram` 是設為 `Auto` 或 `DiffGram`。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-121">However, the `ReadXml` method does raise `ColumnChanged` and `ColumnChanging` events, unless the `XmlReadMode` is set to `DiffGram` or is set to `Auto` when the XML document being read is a `DiffGram`.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ec5e8-122">如果從中引發 `DataSet` 事件的 `RowChanged` 已修改了資料，就可能會發生資料損毀。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-122">Data corruption can occur if data is modified in a `DataSet` from which the `RowChanged` event is raised.</span></span> <span data-ttu-id="ec5e8-123">如果發生這類資料損毀，就不會引發任何例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-123">No exception will be raised if such data corruption occurs.</span></span>  
  
## <a name="additional-related-events"></a><span data-ttu-id="ec5e8-124">其他相關事件</span><span class="sxs-lookup"><span data-stu-id="ec5e8-124">Additional Related Events</span></span>  
 <span data-ttu-id="ec5e8-125"><xref:System.Data.DataTable.Constraints%2A> 屬性會保存 <xref:System.Data.ConstraintCollection> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-125">The <xref:System.Data.DataTable.Constraints%2A> property holds a <xref:System.Data.ConstraintCollection> instance.</span></span> <span data-ttu-id="ec5e8-126"><xref:System.Data.ConstraintCollection> 類別會公開 <xref:System.Data.ConstraintCollection.CollectionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-126">The <xref:System.Data.ConstraintCollection> class exposes a <xref:System.Data.ConstraintCollection.CollectionChanged> event.</span></span> <span data-ttu-id="ec5e8-127">從 `ConstraintCollection` 加入、修改或移除條件約束 (Constraint) 時，就會引發這個事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-127">This event fires when a constraint is added, modified, or removed from the `ConstraintCollection`.</span></span>  
  
 <span data-ttu-id="ec5e8-128"><xref:System.Data.DataTable.Columns%2A> 屬性會保存 <xref:System.Data.DataColumnCollection> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-128">The <xref:System.Data.DataTable.Columns%2A> property holds a <xref:System.Data.DataColumnCollection> instance.</span></span> <span data-ttu-id="ec5e8-129">`DataColumnCollection` 類別會公開 <xref:System.Data.DataColumnCollection.CollectionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-129">The `DataColumnCollection` class exposes a <xref:System.Data.DataColumnCollection.CollectionChanged> event.</span></span> <span data-ttu-id="ec5e8-130">從 `DataColumn` 加入、修改或移除 `DataColumnCollection` 時，就會引發這個事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-130">This event fires when a `DataColumn` is added, modified, or removed from the `DataColumnCollection`.</span></span> <span data-ttu-id="ec5e8-131">對名稱、型別、運算式或資料行序數位置所做的變更，都屬於會導致引發此事件的修改作業。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-131">Modifications that cause the event to fire include changes to the name, type, expression or ordinal position of a column.</span></span>  
  
 <span data-ttu-id="ec5e8-132"><xref:System.Data.DataSet.Tables%2A> 的 <xref:System.Data.DataSet> 屬性會保存 <xref:System.Data.DataTableCollection> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-132">The <xref:System.Data.DataSet.Tables%2A> property of a <xref:System.Data.DataSet> holds a <xref:System.Data.DataTableCollection> instance.</span></span> <span data-ttu-id="ec5e8-133">`DataTableCollection` 類別會公開 `CollectionChanged` 和 `CollectionChanging` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-133">The `DataTableCollection` class exposes both a `CollectionChanged` and a `CollectionChanging` event.</span></span> <span data-ttu-id="ec5e8-134">從 `DataTable` 加入或移除 `DataSet` 時，就會引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-134">These events fire when a `DataTable` is added to or removed from the `DataSet`.</span></span>  
  
 <span data-ttu-id="ec5e8-135">對 `DataRows` 所做的變更也可能觸發相關 <xref:System.Data.DataView> 的事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-135">Changes to `DataRows` can also trigger events for an associated <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ec5e8-136">`DataView` 類別會公開 <xref:System.Data.DataView.ListChanged> 事件，此事件會在 `DataColumn` 值變更或檢視的組合或排序次序變更時引發。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-136">The `DataView` class exposes a <xref:System.Data.DataView.ListChanged> event that fires when a `DataColumn` value changes or when the composition or sort order of the view changes.</span></span> <span data-ttu-id="ec5e8-137"><xref:System.Data.DataRowView> 類別會公開 <xref:System.Data.DataRowView.PropertyChanged> 事件，此事件會在相關的 `DataColumn` 值變更時引發。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-137">The <xref:System.Data.DataRowView> class exposes a <xref:System.Data.DataRowView.PropertyChanged> event that fires when an associated `DataColumn` value changes.</span></span>  
  
## <a name="sequence-of-operations"></a><span data-ttu-id="ec5e8-138">作業序列</span><span class="sxs-lookup"><span data-stu-id="ec5e8-138">Sequence of Operations</span></span>  
 <span data-ttu-id="ec5e8-139">這是發生在加入、修改或刪除 `DataRow` 後的作業序列：</span><span class="sxs-lookup"><span data-stu-id="ec5e8-139">Here is the sequence of operations that occur when a `DataRow` is added, modified, or deleted:</span></span>  
  
1.  <span data-ttu-id="ec5e8-140">建立建議的記錄並套用任何變更。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-140">Create the proposed record and apply any changes.</span></span>  
  
2.  <span data-ttu-id="ec5e8-141">請檢查非運算式資料行的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-141">Check constraints for non-expression columns.</span></span>  
  
3.  <span data-ttu-id="ec5e8-142">依需要引發 `RowChanging` 或 `RowDeleting` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-142">Raise the `RowChanging` or `RowDeleting` events as applicable.</span></span>  
  
4.  <span data-ttu-id="ec5e8-143">將建議的記錄設定為目前的記錄。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-143">Set the proposed record to be the current record.</span></span>  
  
5.  <span data-ttu-id="ec5e8-144">更新任何相關的索引。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-144">Update any associated indexes.</span></span>  
  
6.  <span data-ttu-id="ec5e8-145">針對相關的 `ListChanged` 物件引發 `DataView` 事件；針對相關的 `PropertyChanged` 物件引發 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-145">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects.</span></span>  
  
7.  <span data-ttu-id="ec5e8-146">評估所有的運算式資料行，但延遲檢查這些資料行上所有的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-146">Evaluate all expression columns, but delay checking any constraints on these columns.</span></span>  
  
8.  <span data-ttu-id="ec5e8-147">針對相關的 `ListChanged` 物件引發 `DataView` 事件；針對受到運算式資料行評估影響的相關 `PropertyChanged` 物件引發 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-147">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects affected by the expression column evaluations.</span></span>  
  
9. <span data-ttu-id="ec5e8-148">依需要引發 `RowChanged` 或 `RowDeleted` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-148">Raise `RowChanged` or `RowDeleted` events as applicable.</span></span>  
  
10. <span data-ttu-id="ec5e8-149">請檢查運算式資料行的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-149">Check constraints on expression columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec5e8-150">對運算式資料行的變更永遠不會引發 `DataTable` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-150">Changes to expression columns never raise `DataTable` events.</span></span> <span data-ttu-id="ec5e8-151">對運算式資料行的變更僅會引發 `DataView` 和 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-151">Changes to expression columns only raise `DataView` and `DataRowView` events.</span></span> <span data-ttu-id="ec5e8-152">運算式資料行可能會相依於其他多個資料行，而且可在單一的 `DataRow` 作業期間進行多次評估。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-152">Expression columns can have dependencies on multiple other columns, and can be evaluated multiple times during a single `DataRow` operation.</span></span> <span data-ttu-id="ec5e8-153">每個運算式評估都會引發事件；在運算式資料行受到影響時，單一的 `DataRow` 作業則可能會引發多個 `ListChanged` 和 `PropertyChanged` 事件，而相同的運算式資料行則可能會包含多個事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-153">Each expression evaluation raises events, and a single `DataRow` operation can raise multiple `ListChanged` and `PropertyChanged` events when expression columns are affected, possibly including multiple events for the same expression column.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ec5e8-154">請勿在 <xref:System.NullReferenceException> 事件處理常式內部擲回 `RowChanged`。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-154">Do not throw a <xref:System.NullReferenceException> within the `RowChanged` event handler.</span></span> <span data-ttu-id="ec5e8-155">如果在 <xref:System.NullReferenceException> 的 `RowChanged` 事件內部擲回 `DataTable`，將會損毀 `DataTable`。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-155">If a <xref:System.NullReferenceException> is thrown within the `RowChanged` event of a `DataTable`, then the `DataTable` will be corrupted.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ec5e8-156">範例</span><span class="sxs-lookup"><span data-stu-id="ec5e8-156">Example</span></span>  
 <span data-ttu-id="ec5e8-157">下列範例示範如何建立 `RowChanged`、`RowChanging`、`RowDeleted`、`RowDeleting`、`ColumnChanged`、`ColumnChanging`、`TableNewRow`、`TableCleared` 和 `TableClearing` 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-157">The following example demonstrates how to create event handlers for the `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, and `TableClearing` events.</span></span> <span data-ttu-id="ec5e8-158">每個事件處理常式在引發時，都會將輸出顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ec5e8-158">Each event handler displays output in the console window when it is fired.</span></span>  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ec5e8-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec5e8-159">See Also</span></span>  
 [<span data-ttu-id="ec5e8-160">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="ec5e8-160">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="ec5e8-161">處理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="ec5e8-161">Handling DataAdapter Events</span></span>](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="ec5e8-162">處理 DataSet 的事件</span><span class="sxs-lookup"><span data-stu-id="ec5e8-162">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="ec5e8-163">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ec5e8-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
