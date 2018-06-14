---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: c374261ad3702294f5720edb7881e21ba79d85bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764732"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)
在建立於實體之間的關聯性上巡覽。  
  
## <a name="syntax"></a>語法  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>引數  
 `instance-expresssion`  
 實體的執行個體。  
  
 `relationship-type`  
 關聯性的型別名稱，來自概念結構定義語言 (CSDL) 檔案。 `relationship-type`是限定為\<命名空間 >。\<關聯性類型名稱 >。  
  
 `to`  
 關聯性的結束。  
  
 `from`  
 關聯性的開始。  
  
## <a name="return-value"></a>傳回值  
 如果結束端的基數為 1，傳回值將會是 `Ref<T>`。 如果結束端的基數為 n，傳回值將會是 `Collection<Ref<T>>`。  
  
## <a name="remarks"></a>備註  
 關聯性是 [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM) 中的第一類建構。 您可在兩個以上的實體類型之間建立關聯性，讓使用者能夠巡覽其中一端 (實體) 到另一端的關聯性。 關聯性中的名稱解析沒有模稜兩可情況時，可以有條件地選擇`from` 和 `to` 。  
  
 NAVIGATE 在 O 和 C 空間中有效。  
  
 導覽建構的一般形式如下：  
  
 navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )  
  
 例如：  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 其中 OrderCustomer 是 `relationship`，而 Customer 和 Order 則是關聯性的 `to-end` (客戶) 和 `from-end` (訂單)。 如果 OrderCustomer 是 n:1 關聯性，那麼巡覽運算式的結果型別是 Ref\<客戶 >。  
  
 這個運算式更簡單的形式如下：  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 同樣地，在下列形式的查詢中，巡覽運算式將會產生集合 < Ref\<順序 >>。  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 此執行個體運算式必須是實體/參考型別。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 NAVIGATE 運算子在建立於 Address 和 SalesOrderHeader 實體類型之間的關聯性上巡覽。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [如何： 巡覽關聯性巡覽運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
