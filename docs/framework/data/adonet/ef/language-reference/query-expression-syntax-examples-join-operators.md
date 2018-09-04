---
title: 查詢運算式語法範例：聯結運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 4db511d74c4cce82bfd010f77cb1580dbb704b41
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501894"
---
# <a name="query-expression-syntax-examples-join-operators"></a>查詢運算式語法範例：聯結運算子
在以彼此沒有可瀏覽關聯性之資料來源 (例如關聯式資料庫資料表) 為目標的查詢中，聯結 (Join) 是一項重要的作業。 兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯。 如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
 本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.GroupJoin%2A>並<xref:System.Linq.Enumerable.Join%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)透過查詢運算式語法。 這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 本主題中的範例使用下列`using` / `Imports`陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>範例  
 下列範例會在 SalesOrderHeader 和 SalesOrderDetail 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一客戶的定單數目。 群組聯結是左外部聯結的對等項目，它會傳回第一個 (左) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>範例  
 下列範例會在 Contact 和 SalesOrderHeader 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一連絡人的定單數目。 然後顯示每一連絡人的訂單數目和 ID。  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a>範例  
 下列範例會針對 Contact 和 SalesOrderHeader 資料表執行 <xref:System.Linq.Enumerable.GroupJoin%2A>。 群組聯結是左外部聯結的對等項目，它會傳回第一個 (左) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>範例  
 下列範例會針對 SalesOrderHeader 和 SalesOrderDetail 資料表執行聯結，以便取得八月的線上訂單資訊。  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
