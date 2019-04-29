---
title: HOW TO：實作 CopyToDataTable<T>，其中泛型型別 T 不是 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 120b4bf22e310bee73ba006cfe5a060d0ecd9d65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667011"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="b7ef7-102">HOW TO：實作 CopyToDataTable\<T > 其中泛型型別 T 不是 DataRow</span><span class="sxs-lookup"><span data-stu-id="b7ef7-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="b7ef7-103"><xref:System.Data.DataTable> 物件通常用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="b7ef7-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法會採用查詢的結果並將資料複製到 <xref:System.Data.DataTable> 中，然後此物件便可用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="b7ef7-105">但是，<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法只會在通用參數 <xref:System.Collections.Generic.IEnumerable%601> 為 `T` 型別的 <xref:System.Data.DataRow> 來源上運作。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b7ef7-106">雖然這樣非常有用，但是資料表卻無法從一序列的純量型別、傳回匿名型別的查詢或執行資料表聯結的查詢建立。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="b7ef7-107">此主題描述如何實作能接受通用參數 `CopyToDataTable<T>` 型別不是 `T` 的兩個自訂 <xref:System.Data.DataRow> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b7ef7-108">可以從 <xref:System.Data.DataTable> 來源建立 <xref:System.Collections.Generic.IEnumerable%601> 的邏輯會包含在 `ObjectShredder<T>` 類別中，然後再包裝到兩個多載的 `CopyToDataTable<T>` 擴充方法中。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="b7ef7-109">`Shred` 類別的 `ObjectShredder<T>` 方法會傳回填滿的 <xref:System.Data.DataTable> 並接受三個輸入參數：<xref:System.Collections.Generic.IEnumerable%601> 來源、<xref:System.Data.DataTable> 以及 <xref:System.Data.LoadOption> 列舉。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="b7ef7-110">所傳回 <xref:System.Data.DataTable> 的最初結構描述是根據 `T` 型別之結構描述而來的。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="b7ef7-111">如果也提供現有的資料表做為輸入參數，則此結構描述必須與 `T` 型別的結構描述一致。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="b7ef7-112">在所傳回的資料表中，`T` 型別的每一個公用屬性和欄位都會轉換為 <xref:System.Data.DataColumn>。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="b7ef7-113">如果來源序列包含衍生自 `T` 的型別，則傳回的資料表結構描述會因為額外的公用屬性或欄位展開。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="b7ef7-114">如需使用自訂 `CopyToDataTable<T>` 方法的範例，請參閱[從查詢建立 DataTable](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="b7ef7-115">在應用程式中實作自訂的 CopyToDataTable\<T> 方法</span><span class="sxs-lookup"><span data-stu-id="b7ef7-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="b7ef7-116">實作 `ObjectShredder<T>` 類別以從 <xref:System.Data.DataTable> 來源建立 <xref:System.Collections.Generic.IEnumerable%601>：</span><span class="sxs-lookup"><span data-stu-id="b7ef7-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="b7ef7-117">上述範例假設 `DataColumn` 的屬性都不是可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="b7ef7-118">若要處理具有可為 Null 型別的屬性，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b7ef7-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="b7ef7-119">在類別中實作自訂 `CopyToDataTable<T>` 擴充方法：</span><span class="sxs-lookup"><span data-stu-id="b7ef7-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="b7ef7-120">將 `ObjectShredder<T>` 類別和 `CopyToDataTable<T>` 擴充方法新增到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b7ef7-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="b7ef7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7ef7-121">See also</span></span>

- [<span data-ttu-id="b7ef7-122">從查詢建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="b7ef7-122">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="b7ef7-123">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b7ef7-123">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
