---
title: LINQ to Entities 查詢中的標準查詢運算子
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 302fa281767fc95e9a9a2192382034b3a519cd92
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884865"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>LINQ to Entities 查詢中的標準查詢運算子
在查詢中，您可以指定要從資料來源擷取的資訊。 此外，查詢也可以指定該項資訊傳回之前應該如何排序、分組和成形。 LINQ 提供一組可在查詢中使用的標準查詢方法。 這些方法大多操作序列;在此情況下，序列是其類型會實作的物件<xref:System.Collections.Generic.IEnumerable%601>介面或<xref:System.Linq.IQueryable%601>介面。 標準查詢運算子的查詢功能包括篩選、投影、彙總、排序、群組、分頁等等。 某些更常用的標準查詢運算子具有專用的關鍵字語法，因此可以使用查詢運算式語法來呼叫它們。 相較於以方法為根據的同等項目，查詢運算式是一個不同且更具可讀性之表示查詢的方式。 查詢運算式子句會在編譯時期轉譯成查詢方法的呼叫。 如需標準查詢運算子具有相等的查詢運算式子句的清單，請參閱 <<c0> [ 標準查詢運算子概觀](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
 並非所有的標準查詢運算子在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中都有支援。 如需詳細資訊，請參閱 <<c0> [ 支援和不受支援的 LINQ 方法 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)。 本主題提供的資訊是有關 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 特定的標準查詢運算子。 如需有關已知問題[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢，請參閱[已知問題在 LINQ to Entities 和考量](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)。  
  
## <a name="projection-and-filtering-methods"></a>投影及篩選方法  
 *投影*是指轉換的結果集所需的格式項目。 例如，您可以從結果集中的每一個物件投影您需要的屬性子集，也可以投影屬性並針對它執行數學計算，或是從結果集投影整個物件。 投影方法為 `Select` 和 `SelectMany`。  
  
 *篩選*指的是作業的結果集限制為包含只有在符合指定的條件的元素。 篩選方法為 `Where`。  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 中支援大多數投影和篩選方法的多載，但是接受位置引數的多載除外。  
  
## <a name="join-methods"></a>聯結方法  
 在以彼此沒有可瀏覽關聯性之資料來源為目標的查詢中，聯結是一項重要的作業。 兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性 (Attribute) 或屬性 (Property) 之物件的關聯。 聯結方法為 `Join` 和 `GroupJoin`。  
  
 大多數聯結方法的多載都有支援，但是使用 <xref:System.Collections.Generic.IEqualityComparer%601> 的多載除外。 這是因為比較子 (Comparer) 無法轉譯成資料來源。  
  
## <a name="set-methods"></a>Set 方法  
 LINQ 中的 Set 作業是指一種查詢作業，這種作業會讓其結果集根據相同或另一個集合中是否有同等項目存在而定。 Set 方法為 `All`、`Any`、`Concat`、`Contains`、`DefaultIfEmpty`、`Distinct`、`EqualAll`、`Except`、`Intersect` 和 `Union`。  
  
 大多數 Set 方法的多載在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 中都有支援，但是與 LINQ to Objects 相較之下會有一些行為上的差異。 不過，設定使用的方法<xref:System.Collections.Generic.IEqualityComparer%601>不支援，因為比較子無法轉譯成資料來源。  
  
## <a name="ordering-methods"></a>排序方法  
 排序指的是根據一或多個屬性來排序結果集的項目。 藉由指定一個以上的排序準則，就可以中斷群組內的繫結。  
  
 大多數排序方法的多載都有支援，但是使用 <xref:System.Collections.Generic.IComparer%601> 的多載除外。 這是因為比較子 (Comparer) 無法轉譯成資料來源。 排序方法為 `OrderBy`、`OrderByDescending`、`ThenBy`、`ThenByDescending` 和 `Reverse`。  
  
 因為查詢是在資料來源上執行，所以排序行為可能會與 CLR 中執行的查詢不同。 這是因為排序選項 (例如大小寫排序、漢字排序和 null 排序) 可以在資料來源中設定。 視資料來源的不同，這些排序選項可能會產生與 CLR 中不同的結果。  
  
 如果您在一個以上的排序作業中指定相同的索引鍵選取器，將會產生重複的排序。 這是無效的，而且將會擲回例外狀況。  
  
## <a name="grouping-methods"></a>群組方法  
 群組指的是將資料放在群組中，好讓每一個群組中的項目都可共用共同的屬性。 此群組方法為 `GroupBy`。  
  
 大多數群組方法的多載都有支援，但是使用 <xref:System.Collections.Generic.IEqualityComparer%601> 的多載除外。 這是因為比較子 (Comparer) 無法轉譯成資料來源。  
  
 群組方法會使用索引鍵選取器的不同子查詢對應到資料來源。 索引鍵選取器比較子查詢是使用資料來源的語意來執行，包括與比較 `null` 值有關的問題。  
  
## <a name="aggregate-methods"></a>彙總方法  
 彙總運算會計算值集合中的單一值。 例如，當您使用一個月中每天的溫度值來計算每天平均溫度時，您就執行了一項彙總運算。 彙總方法為 `Aggregate`、`Average`、`Count`、`LongCount`、`Max`、`Min` 和 `Sum`。  
  
 大多數彙總方法的多載都有支援。 如果是與 null 值有關的行為，彙總方法會使用資料來源語意。 當牽涉到 null 值時的彙總方法行為可能會有不同 (根據使用哪一個後端資料來源而定)。 使用資料來源語意的彙總方法行為也可能會與 CLR 方法預期的行為不同。 例如，SQL Server 上 `Sum` 方法的預設行為是要忽略所有 null 值，而不是擲回例外狀況。  
  
 彙總產生的所有例外狀況 (例如 `Sum` 函式中的溢位) 會在具體化查詢結果期間顯示為資料來源例外狀況或是 Entity Framework 例外狀況。  
  
 對於牽涉到序列計算的方法而言 (例如 `Sum` 或 `Average`)，實際的計算會在伺服器上執行。 因此，型別轉換和精確度的喪失可能會在伺服器上發生，而且結果可能會與使用 CLR 語意所預期的結果不同。  
  
 null/非 null 值之彙總方法的預設行為顯示於下表：  
  
|方法|無資料|所有 null 值|某些 null 值|無 null 值|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|傳回 null。|傳回 null。|傳回序列中非 Null 值的平均值。|計算數值序列的平均值。|  
|`Count`|傳回 0|傳回序列中 null 值的數目。|傳回序列中 null 值與非 null 值的數目。|傳回序列中的項目數。|  
|`Max`|傳回 null。|傳回 null。|傳回序列中最大的非 null 值。|傳回序列中的最大值。|  
|`Min`|傳回 null。|傳回 null。|傳回序列中最小的非 null 值。|傳回序列中的最小值。|  
|`Sum`|傳回 null。|傳回 null。|傳回序列中非 null 值的總和。|計算數值序列的總和。|  
  
## <a name="type-methods"></a>型別方法  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 的內容中支援處理型別轉換和測試的兩個 LINQ 方法。 這表示，只有支援的型別是對應到適當 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 型別的型別。 如需這些類型的清單，請參閱 <<c0> [ 概念模型型別 (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)。 型別方法為 `Convert` 和 `OfType`。  
  
 實體類型支援 `OfType`。 概念模型基本型別支援 `Convert`。  也支援 C# `is` 和 `as` 方法。  
  
## <a name="paging-methods"></a>分頁方法  
 分頁作業從序列中傳回單一項目或多個項目。 支援的分頁方法為`First`， `FirstOrDefault`， `Single`， `SingleOrDefault`， `Skip`，和`Take`。  
  
 不支援的一些分頁方法，因為無法將函式對應至資料來源，或缺少隱含的資料來源上的集合排序。 傳回預設值的方法限制為具有 null 預設值的概念模型基本型別及參考型別。 在空序列上執行的分頁方法將會傳回 null。  
  
## <a name="see-also"></a>另請參閱  
 [支援和不支援的 LINQ 方法 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [標準查詢運算子概觀](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
