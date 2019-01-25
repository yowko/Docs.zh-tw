---
title: LINQ to Entities 中的已知問題和考量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: ca67a01d8f1bc76773a7794169e93d026fe222d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717957"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>LINQ to Entities 中的已知問題和考量
本節提供有關 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢已知問題的資訊。  
  
-   [無法快取的 LINQ 查詢](#LINQQueriesThatAreNotCached)  
  
-   [排序資訊遺失](#OrderingInfoLost)  
  
-   [不支援不帶正負號的整數](#UnsignedIntsUnsupported)  
  
-   [型別轉換錯誤](#TypeConversionErrors)  
  
-   [不支援參考非純量變數](#RefNonScalarClosures)  
  
-   [使用 SQL Server 2000 的巢狀的查詢可能會失敗](#NestedQueriesSQL2000)  
  
-   [投影至匿名型別](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>不能快取的 LINQ 查詢  
 從 .NET Framework 4.5 開始會自動快取 LINQ to Entities 查詢。 不過，不會自動快取將 `Enumerable.Contains`運算子套用至記憶體中集合的 LINQ to Entities 查詢。 此外也不允許在已編譯的 LINQ 查詢中參數化記憶體中的集合。  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>排序資訊遺失  
 在針對相容性層級設定為 "80" 的 [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] 資料庫執行的某些查詢中，將資料行投影到匿名型別將會造成排序資訊遺失。  如果 order-by 清單中的資料行名稱與 selector 中的資料行名稱相符，就會發生這種情況，如以下範例所示：  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>不支援不帶正負號的整數  
 不支援在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中指定不帶正負號的整數型別，因為 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 不支援不帶正負號的整數。 如果您指定的不帶正負號的整數，<xref:System.ArgumentException>將會擲回例外狀況在查詢運算式轉譯期間，在下列範例所示。 此範例會查詢 ID 為 48000 的訂單。  
  
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
>  支援參考純量變數的集合。  
  
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
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
