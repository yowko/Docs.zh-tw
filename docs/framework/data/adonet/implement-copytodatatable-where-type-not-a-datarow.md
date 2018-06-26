---
title: 如何：實作泛型型別 T 不是 DataRow 的 CopyToDataTable&lt;T&gt;
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 106442c26f0bb02cf57dcc5d8b1ac534c70320ac
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753509"
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a>如何：實作泛型型別 T 不是 DataRow 的 CopyToDataTable&lt;T&gt;
<xref:System.Data.DataTable> 物件通常用於資料繫結。 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法會採用查詢的結果並將資料複製到 <xref:System.Data.DataTable> 中，然後此物件便可用於資料繫結。 但是，<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法只會在通用參數 <xref:System.Collections.Generic.IEnumerable%601> 為 `T` 型別的 <xref:System.Data.DataRow> 來源上運作。 雖然這樣非常有用，但是資料表卻無法從一序列的純量型別、傳回匿名型別的查詢或執行資料表聯結的查詢建立。  
  
 此主題描述如何實作能接受通用參數 `CopyToDataTable<T>` 型別不是 `T` 的兩個自訂 <xref:System.Data.DataRow> 擴充方法。 可以從 <xref:System.Data.DataTable> 來源建立 <xref:System.Collections.Generic.IEnumerable%601> 的邏輯會包含在 `ObjectShredder<T>` 類別中，然後再包裝到兩個多載的 `CopyToDataTable<T>` 擴充方法中。 `Shred` 類別的 `ObjectShredder<T>` 方法會傳回填滿的 <xref:System.Data.DataTable> 並接受三個輸入參數：<xref:System.Collections.Generic.IEnumerable%601> 來源、<xref:System.Data.DataTable> 以及 <xref:System.Data.LoadOption> 列舉。 所傳回 <xref:System.Data.DataTable> 的最初結構描述是根據 `T` 型別之結構描述而來的。 如果也提供現有的資料表做為輸入參數，則此結構描述必須與 `T` 型別的結構描述一致。 在所傳回的資料表中，`T` 型別的每一個公用屬性和欄位都會轉換為 <xref:System.Data.DataColumn>。 如果來源序列包含衍生自 `T` 的型別，則傳回的資料表結構描述會因為額外的公用屬性或欄位展開。  
  
 如需使用自訂 `CopyToDataTable<T>` 方法的範例，請參閱[從查詢建立 DataTable](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)。  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>在應用程式中實作自訂的 CopyToDataTable\<T> 方法  
  
1.  實作 `ObjectShredder<T>` 類別以從 <xref:System.Data.DataTable> 來源建立 <xref:System.Collections.Generic.IEnumerable%601>：  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    上述範例假設 `DataColumn` 的屬性都不是可為 Null 的型別。 若要處理具有可為 Null 型別的屬性，請使用下列程式碼：

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  在類別中實作自訂 `CopyToDataTable<T>` 擴充方法：  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  將 `ObjectShredder<T>` 類別和 `CopyToDataTable<T>` 擴充方法新增到應用程式中。  
  
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
  
## <a name="see-also"></a>請參閱  
 [從查詢建立 DataTable](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
