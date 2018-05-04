---
title: 查詢計畫快取 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 0e00d7f9382fca2af630a8e1d50a5cde5178da05
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="query-plan-caching-entity-sql"></a>查詢計畫快取 (Entity SQL)
每當嘗試執行查詢時，查詢管線就會查閱它的查詢快取計畫，以查看精確的查詢是否已編譯且可用。 如果確實如此，它會重複使用快取的計畫，而不是建立新的計畫。 如果查詢計畫快取中找不到相符項目，就會編譯及快取此查詢。 查詢是由它的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 文字和參數集合 (名稱和型別) 所識別。 所有的文字比較都會區分大小寫。  
  
## <a name="configuration"></a>組態  
 查詢計畫快取可透過 <xref:System.Data.EntityClient.EntityCommand> 來設定。  
  
 若要透過 <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> 來啟用或停用查詢計畫快取，請將此屬性設定為 `true` 或 `false`。 針對不太可能使用一次以上的個別動態查詢停用計畫快取時，將會提升效能。  
  
 您可以透過 <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> 來啟用查詢計畫快取。  
  
## <a name="recommended-practice"></a>建議的作法  
 一般來說，應該避免動態查詢。 下列動態查詢範例容易受到 SQL 插入式攻擊的侵害，因為它會在沒有任何驗證的情況下直接接受使用者輸入。  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 如果您使用動態產生的查詢，請考慮停用查詢計畫快取，避免針對不太可能重複使用的快取項目產生不必要的記憶體耗用量。  
  
 靜態查詢和參數化查詢上的查詢計畫快取可提供效能方面的優點。 下列是靜態查詢的範例：  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 如果是查詢計畫快取所要適當比對的查詢，這些查詢應該要符合以下規定：  
  
-   查詢文字應該是固定模式，最好是某個固定字串或資源。  
  
-   每當必須傳遞使用者提供的值時，就應該使用 <xref:System.Data.EntityClient.EntityParameter> 或 <xref:System.Data.Objects.ObjectParameter>。  
  
 您應該避免下列查詢模式，這樣會耗用查詢計畫快取中的位置，而這是不必要的：  
  
-   變更為文字中的字母大小寫。  
  
-   變更為泛空白字元。  
  
-   變更為常值。  
  
-   變更為註解內的文字。  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
