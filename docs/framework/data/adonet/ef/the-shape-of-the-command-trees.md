---
title: 命令樹的形狀
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 8368354049a77a56a5aa54ab500619576f41b0dc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854272"
---
# <a name="the-shape-of-the-command-trees"></a>命令樹的形狀

SQL 產生模組負責根據給定輸入查詢命令樹運算式，產生後端特定的 SQL 查詢。 本章節將討論查詢命令樹的特性、屬性和結構。

## <a name="query-command-trees-overview"></a>查詢命令樹概觀

查詢命令樹是某個查詢的物件模型表示法。 查詢命令樹有兩個用途：

- 表示針對 Entity Framework 所指定的輸入查詢。

- 為了表示提供給提供者並針對後端描述查詢的輸出查詢。

查詢命令樹可支援比 SQL:1999 相容的查詢更為豐富的語意，包括使用巢狀集合和型別作業的支援，就像檢查某個實體是否具有特定型別，或者根據型別篩選集合。

DBQueryCommandTree.Query 屬性是描述查詢邏輯之運算式樹狀架構的根。 DBQueryCommandTree.Parameters 屬性包含用於查詢的參數清單。 由 DbExpression 物件所組成的運算式。

DbExpression 物件代表某些計算。 組成查詢運算式的 Entity Framework 會提供數種運算式，包括常數、變數、函式、函式和標準關係運算子，例如篩選和聯結。 每個 DbExpression 物件都有一個 ResultType 屬性，代表該運算式所產生的結果類型。 這個型別會表示為 TypeUsage。

## <a name="shapes-of-the-output-query-command-tree"></a>輸出查詢命令樹的形狀

輸出查詢命令樹緊密地代表關聯式 (SQL) 查詢，而且與查詢命令樹所套用的規則相較之下，前者會遵守更為嚴格的規則。 這些通常包含可輕鬆轉譯為 SQL 的建構。

輸入命令樹會針對概念模型來表示，概念模型可支援導覽屬性、多個實體之間的關聯及繼承。 輸出命令樹會針對儲存體模型來表示。 輸入命令樹可讓您投射巢狀集合，但輸出命令樹則不行。

輸出查詢命令樹是使用可用的 DbExpression 物件子集所建置，而且即使是該子集中的某些運算式也是有使用上的限制。

型別作業 (就像檢查給定運算式是否具有特定型別，或是根據型別篩選集合) 不會出現在輸出命令樹中。

在輸出命令樹狀中，只有傳回布林值的運算式會用於投射，而且只適用於需要述詞 (如 filter 或 case 陳述式) 之運算式中的述詞。

輸出查詢命令樹的根為 DbProjectExpression 物件。

### <a name="expression-types-not-present-in-output-query-command-trees"></a>輸出查詢命令樹中未出現運算式型別

下列運算式型別在輸出查詢命令樹中無效，而且不需要由提供者來處理：

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>運算式限制和備註

許多運算式在輸出查詢命令樹中，只能以限制的方式來使用：

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

下列是可以傳遞的函式型別：

- Edm 命名空間所辨識的標準函式。

- BuiltInAttribute 所辨識的內建 (存放區) 函式。

- 使用者定義函式。

標準函式（如需詳細資訊，請參閱[標準](./language-reference/canonical-functions.md)函式）會指定為 Entity Framework 的一部分，而提供者應根據這些規格提供標準函式的執行。 存放區函式是根據對應之提供者資訊清單中的規格。 使用者定義函式是根據 SSDL 中的規格。

此外，具有 NiladicFunction 屬性的函式沒有任何引數，而且轉譯時結尾不應該有括號。  也就是 *\<functionName* *\<* >，而不是 functionName > （）。

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbNewInstanceExpression 只能發生在下列兩個案例中：

- 當做 DbProjectExpression 的 Projection 屬性。  當依照這類情況使用時，要遵守下列限制：

  - 結果型別必須是資料列型別。

  - 它的每一個引數都是一個運算式，可產生具有基本型別的結果。 一般來說，每一個引數都是純量運算式，例如透過 DbVariableReferenceExpression 的 PropertyExpression、函式引動過程，或是透過 DbVariableReferenceExpression 或函式引動過程之 DbPropertyExpression 的算術運算。 但是，代表純量子查詢的運算式也可以出現在 DbNewInstanceExpression 的引數清單中。 表示純量子查詢的運算式是運算式樹狀架構，代表只傳回一個資料列，以及一個具有 DbElementExpression 物件根之基本型別資料行的子查詢

- 有了集合傳回型別，就可以定義當做引數提供之運算式的新集合。

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

DbVariableReferenceExpression 必須是 DbPropertyExpression 節點的子系。

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

DbGroupByExpression 的 Aggregates 屬性只能擁有 DbFunctionAggregate 型別的項目。 沒有其他任何彙總型別。

#### <a name="dblimitexpression"></a>DbLimitExpression

屬性限制只能是 DbConstantExpression 或 DbParameterReferenceExpression。 此外，WithTies 屬性在 .NET Framework 3.5 版中一定是 false。

#### <a name="dbscanexpression"></a>DbScanExpression

在輸出命令樹中使用時，DbScanExpression 實際上代表對資料表、視圖或存放區查詢（以 EntitySetBase：： Target 表示）的掃描。

如果目標的中繼資料屬性「定義查詢」為非 null，則它代表一個查詢，它是以存放區架構定義中指定的提供者特定語言（或方言）提供給該中繼資料屬性的查詢文字。

否則，目標會代表資料表或檢視表。 其架構前置詞位於 "Schema" 中繼資料屬性中（如果不是 null），否則為實體容器名稱。  資料表或視圖名稱是 "Table" 中繼資料屬性（如果不是 null），否則為實體集基底的 Name 屬性。

所有的這些屬性都來自於存放結構定義檔案 (SSDL) 中對應 EntitySet 的定義。

### <a name="using-primitive-types"></a>使用基本型別

在輸出命令樹中參考基本型別時，通常會在概念模型的基本型別中參考這些型別。 但是對於某些運算式而言，提供者需要對應的存放區基本型別。 這類運算式的範例包括 DbCastExpression，也可能包括 DbNullExpression (如果提供者需要將 null 轉型為對應的型別)。 在這些情況下，提供者應該根據基本型別種類和它的 Facet，執行與提供者型別的對應。

## <a name="see-also"></a>另請參閱

- [SQL 產生](sql-generation.md)
