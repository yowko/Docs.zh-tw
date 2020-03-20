---
title: 比較語意 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150450"
---
# <a name="comparison-semantics-entity-sql"></a>比較語意 (Entity SQL)
執行以下任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子都會牽涉到型別執行個體的比較：  
  
## <a name="explicit-comparison"></a>明確比較  
 相等運算：  
  
- =  
  
- !=  
  
 排序作業：  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 可為 Null 的運算：  
  
- 是 NULL  
  
- IS NOT NULL  
  
## <a name="explicit-distinction"></a>明確區分  
 相等區分：  
  
- DISTINCT  
  
- GROUP BY  
  
 排序區分：  
  
- 排序依據  
  
## <a name="implicit-distinction"></a>隱含區分  
 Set 作業和述詞 (相等)：  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Item 述詞 (相等)：  
  
- IN  
  
## <a name="supported-combinations"></a>支援的組合  
 以下資料表針對每一種型別顯示比較運算子的所有支援組合：  
  
|**類型**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **不同**|**聯盟**<br /><br /> **相交**<br /><br /> **除了**<br /><br /> **設置**<br /><br /> **重疊**|**在**|**<<|**<br /><br /> **>>|**|**按**|**為空**<br /><br /> **不為空**|  
|-|-|-|-|-|-|-|-|  
|實體類型|參考<sup>文獻 1</sup>|所有屬性<sup>2</sup>|所有屬性<sup>2</sup>|所有屬性<sup>2</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|參考<sup>文獻 1</sup>|  
|複雜類型|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|  
|資料列|所有屬性<sup>4</sup>|所有屬性<sup>4</sup>|所有屬性<sup>4</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|所有屬性<sup>4</sup>|投擲<sup>3</sup>|  
|基本型別|提供者特定|提供者特定|提供者特定|提供者特定|提供者特定|提供者特定|提供者特定|  
|多重集|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|  
|參考|是<sup>5</sup>|是<sup>5</sup>|是<sup>5</sup>|是<sup>5</sup>|Throw|Throw|是<sup>5</sup>|  
|關聯<br /><br /> type|投擲<sup>3</sup>|Throw|Throw|Throw|投擲<sup>3</sup>|投擲<sup>3</sup>|投擲<sup>3</sup>|  
  
 <sup>1</sup>隱式比較給定實體類型實例的引用，如以下示例所示：  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 實體執行個體無法與明確參考相比較。 如果嘗試進行此作業，就會擲回例外狀況。 例如，下列查詢將會擲回例外狀況：  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>複雜類型的屬性在發送到存儲之前被拼合，因此它們變得可比較（只要它們的所有屬性都是可比的）。 另請參閱<sup>4。</sup>  
  
 <sup>3</sup>實體框架運行時檢測不受支援的情況，並在不雇用提供程式/存儲的情況下引發有意義的異常。  
  
 <sup>4</sup>嘗試比較所有屬性。 如果某個屬性具有無法比較的型別 (如文字、ntext 或影像)，可能會擲回伺服器例外狀況。  
  
 <sup>5</sup>比較引用的所有單個元素（這包括實體集名稱和實體類型的所有鍵屬性）。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
