---
title: LINQ to Entities 中的已知問題和考量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150138"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>LINQ to Entities 中的已知問題和考量
本節提供有關 LINQ 到實體查詢的已知問題的資訊。  
  
- [不能快取的 LINQ 查詢](#LINQQueriesThatAreNotCached)  
  
- [排序資訊遺失](#OrderingInfoLost)  
  
- [不支援不帶正負號的整數](#UnsignedIntsUnsupported)  
  
- [類型轉換錯誤](#TypeConversionErrors)  
  
- [不支援參考非純量變數](#RefNonScalarClosures)  
  
- [使用 SQL Server 2000 的巢狀查詢可能失敗](#NestedQueriesSQL2000)  
  
- [投影至匿名型別](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a>不能快取的 LINQ 查詢  
 從 .NET Framework 4.5 開始會自動快取 LINQ to Entities 查詢。 不過，不會自動快取將 `Enumerable.Contains`運算子套用至記憶體中集合的 LINQ to Entities 查詢。 此外也不允許在已編譯的 LINQ 查詢中參數化記憶體中的集合。  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a>排序資訊遺失  
 將列投影到匿名型別將導致某些查詢中針對 SQL Server 2005 資料庫設置為"80"的相容性級別執行的排序資訊丟失。  如果 order-by 清單中的資料行名稱與 selector 中的資料行名稱相符，就會發生這種情況，如以下範例所示：  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a>不支援不帶正負號的整數  
 不支援在 LINQ 到實體查詢中指定未簽名整數類型，因為實體框架不支援未簽名整數。 如果指定未簽名整數，則查詢運算式轉換<xref:System.ArgumentException>期間將引發異常，如以下示例所示。 此範例會查詢 ID 為 48000 的訂單。  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a>型別轉換錯誤  
 在 Visual Basic 中，使用 `CByte` 函式將屬性對應到值為 1 的 SQL Server 位元型別資料行時，將會擲回 <xref:System.Data.SqlClient.SqlException> 並且顯示「算術溢位錯誤」訊息。 以下範例會查詢 AdventureWorks 範例資料庫中的 `Product.MakeFlag` 資料行，並且在重複處理查詢結果時擲回例外狀況。  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a>不支援參考非純量變數  
 不支援在查詢中參考非純量變數，例如實體。 執行這類查詢時，系統會擲回 <xref:System.NotSupportedException> 例外狀況，並且顯示一則訊息，表示「無法建立 `EntityType` 型別的常數值。 在此僅支援基本型別 (『例如 Int32、String 和 Guid』)」。  
  
> [!NOTE]
> 支援參考純量變數的集合。  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>使用 SQL Server 2000 的巢狀查詢可能失敗  
 使用 SQL Server 2000 時，如果 LINQ to Entities 查詢產生三層或更多層深度的巢狀 Transact-SQL 查詢，則查詢可能會失敗。  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a>投影至匿名型別  
 如果您透過在 <xref:System.Data.Objects.ObjectQuery%601.Include%2A> 上使用 <xref:System.Data.Objects.ObjectQuery%601> 方法，將初始查詢路徑定義為包括相關物件，然後使用 LINQ 將傳回的物件投影至匿名型別，則包括方法中所指定的物件不會包括在查詢結果中。  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 若要取得相關物件，請不要將傳回的型別投影至匿名型別。  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>另請參閱

- [林Q 到實體](linq-to-entities.md)
