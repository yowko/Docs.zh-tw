---
title: "泛型 Field 和 SetField 方法 (LINQ to DataSet)"
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
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7f71a6e380730ce3d622437b28a3722793524968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a><span data-ttu-id="89fe6-102">泛型 Field 和 SetField 方法 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="89fe6-102">Generic Field and SetField Methods (LINQ to DataSet)</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="89fe6-103">提供擴充方法，<xref:System.Data.DataRow>類別來存取資料行的值：<xref:System.Data.DataRowExtensions.Field%2A>方法和<xref:System.Data.DataRowExtensions.SetField%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="89fe6-103"> provides extension methods to the <xref:System.Data.DataRow> class for accessing column values: the <xref:System.Data.DataRowExtensions.Field%2A> method and the <xref:System.Data.DataRowExtensions.SetField%2A> method.</span></span> <span data-ttu-id="89fe6-104">這些方法可讓開發人員更容易存取資料行值，尤其是與 Null 值相關的情況。</span><span class="sxs-lookup"><span data-stu-id="89fe6-104">These methods provide easier access to column values for developers, especially regarding null values.</span></span> <span data-ttu-id="89fe6-105"><xref:System.Data.DataSet> 會使用 <xref:System.DBNull.Value> 來代表 Null 值，而 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 則會使用 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 中引進的可為 Null 的型別 (Nullable Type) 支援。</span><span class="sxs-lookup"><span data-stu-id="89fe6-105">The <xref:System.Data.DataSet> uses <xref:System.DBNull.Value> to represent null values, whereas [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] uses the nullable type support introduced in the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="89fe6-106">使用預先存在的資料行存取子中<xref:System.Data.DataRow>需要轉型為適當的類型傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="89fe6-106">Using the pre-existing column accessor in <xref:System.Data.DataRow> requires you to cast the return object to the appropriate type.</span></span> <span data-ttu-id="89fe6-107">如果中的特定欄位<xref:System.Data.DataRow>可為 null，您必須明確檢查是否有 null 值傳回因為<xref:System.DBNull.Value>並隱含地將它轉型為另一個型別會擲回<xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="89fe6-107">If a particular field in a <xref:System.Data.DataRow> can be null, you must explicitly check for a null value because returning <xref:System.DBNull.Value> and implicitly casting it to another type throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="89fe6-108">在下列範例中，如果<xref:System.Data.DataRow.IsNull%2A>方法沒有用來檢查是否有 null 值，會擲回例外狀況，是否索引子傳回<xref:System.DBNull.Value>並嘗試將它轉換成<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="89fe6-108">In the following example, if the <xref:System.Data.DataRow.IsNull%2A> method was not used to check for a null value, an exception would be thrown if the indexer returned <xref:System.DBNull.Value> and tried to cast it to a <xref:System.String>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <span data-ttu-id="89fe6-109"><xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> 會設定 <xref:System.Data.DataRow> 中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="89fe6-109">The <xref:System.Data.DataRowExtensions.Field%2A> method provides access to the column values of a <xref:System.Data.DataRow> and the <xref:System.Data.DataRowExtensions.SetField%2A> sets column values in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="89fe6-110">由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別，因此您不需要明確檢查是否有 Null 值 (如同上一個範例)。</span><span class="sxs-lookup"><span data-stu-id="89fe6-110">Both the <xref:System.Data.DataRowExtensions.Field%2A> method and <xref:System.Data.DataRowExtensions.SetField%2A> method handle nullable types, so you do not have to explicitly check for null values as in the previous example.</span></span> <span data-ttu-id="89fe6-111">此外，這兩種方法都是泛型方法，所以您不需要轉型傳回型別。</span><span class="sxs-lookup"><span data-stu-id="89fe6-111">Both methods are generic methods, also, so you do not have to cast the return type.</span></span>  
  
 <span data-ttu-id="89fe6-112">下列範例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89fe6-112">The following example uses the <xref:System.Data.DataRowExtensions.Field%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 <span data-ttu-id="89fe6-113">請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符。</span><span class="sxs-lookup"><span data-stu-id="89fe6-113">Note that the data type specified in the generic parameter `T` of the <xref:System.Data.DataRowExtensions.Field%2A> method and the <xref:System.Data.DataRowExtensions.SetField%2A> method must match the type of the underlying value.</span></span> <span data-ttu-id="89fe6-114">否則，系統將擲回 <xref:System.InvalidCastException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="89fe6-114">Otherwise, an <xref:System.InvalidCastException> exception will be thrown.</span></span> <span data-ttu-id="89fe6-115">此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="89fe6-115">The specified column name must also match the name of a column in the <xref:System.Data.DataSet>, or an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="89fe6-116">在這兩種情況中，其例外狀況是在執行查詢的資料列舉執行階段中擲回。</span><span class="sxs-lookup"><span data-stu-id="89fe6-116">In both cases, the exception is thrown at run time during the enumeration of the data when the query is executed.</span></span>  
  
 <span data-ttu-id="89fe6-117"><xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不會執行任何型別轉換。</span><span class="sxs-lookup"><span data-stu-id="89fe6-117">The <xref:System.Data.DataRowExtensions.SetField%2A> method itself does not perform any type conversions.</span></span> <span data-ttu-id="89fe6-118">不過，這並不表示不會進行型別轉換。</span><span class="sxs-lookup"><span data-stu-id="89fe6-118">This does not mean, however, that a type conversion will not occur.</span></span> <span data-ttu-id="89fe6-119"><xref:System.Data.DataRowExtensions.SetField%2A>方法會公開[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]行為<xref:System.Data.DataRow>類別。</span><span class="sxs-lookup"><span data-stu-id="89fe6-119">The <xref:System.Data.DataRowExtensions.SetField%2A> method exposes the [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] behavior of the <xref:System.Data.DataRow> class.</span></span> <span data-ttu-id="89fe6-120">無法由型別轉換<xref:System.Data.DataRow>物件和轉換的值然後會儲存到<xref:System.Data.DataRow>物件。</span><span class="sxs-lookup"><span data-stu-id="89fe6-120">A type conversion could be performed by the <xref:System.Data.DataRow> object and the converted value would then be saved to the <xref:System.Data.DataRow> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89fe6-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="89fe6-121">See Also</span></span>  
 <xref:System.Data.DataRowExtensions>
