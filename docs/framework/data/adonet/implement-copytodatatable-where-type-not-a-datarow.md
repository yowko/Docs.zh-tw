---
title: "HOW TO：實作通用型別 T 不是 DataRow 的 CopyToDataTable&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：實作通用型別 T 不是 DataRow 的 CopyToDataTable&lt;T&gt;
<xref:System.Data.DataTable> 物件通常用於資料繫結。  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法會採用查詢的結果並將資料複製到 <xref:System.Data.DataTable> 中，然後此物件便可用於資料繫結。  但是，<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法只會在通用參數 `T` 為 <xref:System.Data.DataRow> 型別的 <xref:System.Collections.Generic.IEnumerable%601> 來源上運作。  雖然這樣非常有用，但是資料表卻無法從一序列的純量型別、傳回匿名型別的查詢或執行資料表聯結的查詢建立。  
  
 此主題描述如何實作能接受通用參數 `T` 型別不是 <xref:System.Data.DataRow> 的兩個自訂 `CopyToDataTable<T>` 擴充方法。  可以從 <xref:System.Collections.Generic.IEnumerable%601> 來源建立 <xref:System.Data.DataTable> 的邏輯會包含在 `ObjectShredder<T>` 類別中，然後再包裝到兩個多載的 `CopyToDataTable<T>` 擴充方法中。  `ObjectShredder<T>` 類別的 `Shred` 方法會傳回填滿的 <xref:System.Data.DataTable> 並接受三個輸入參數：<xref:System.Collections.Generic.IEnumerable%601> 來源、<xref:System.Data.DataTable> 以及 <xref:System.Data.LoadOption> 列舉。  所傳回 <xref:System.Data.DataTable> 的最初結構描述是根據 `T` 型別之結構描述而來的。  如果也提供現有的資料表做為輸入參數，則此結構描述必須與 `T` 型別的結構描述一致。  在所傳回的資料表中，`T` 型別的每一個公用屬性和欄位都會轉換為 <xref:System.Data.DataColumn>。  如果來源序列包含衍生自 `T` 的型別，則傳回的資料表結構描述會因為額外的公用屬性或欄位展開。  
  
 如需使用自訂 `CopyToDataTable<T>` 方法的範例，請參閱[從查詢中建立 DataTable](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)。  
  
### 在應用程式中實作 CopyToDataTable\<T\> 方法  
  
1.  實作 `ObjectShredder<T>` 類別以從 <xref:System.Collections.Generic.IEnumerable%601> 來源建立 <xref:System.Data.DataTable>：  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
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
  
4.  ```c#  
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
  
## 請參閱  
 [從查詢中建立 DataTable](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)   
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)