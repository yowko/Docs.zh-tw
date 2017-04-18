---
title: "命令樹的形狀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 命令樹的形狀
SQL 產生模組負責根據給定輸入查詢命令樹運算式，產生後端特定的 SQL 查詢。  本章節將討論查詢命令樹的特性、屬性和結構。  
  
## 查詢命令樹概觀  
 查詢命令樹是某個查詢的物件模型表示法。  查詢命令樹有兩個用途：  
  
-   為了表示針對 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 所指定的輸入查詢。  
  
-   為了表示提供給提供者並針對後端描述查詢的輸出查詢。  
  
 查詢命令樹可支援比 SQL:1999 相容的查詢更為豐富的語意，包括使用巢狀集合和型別作業的支援，就像檢查某個實體是否具有特定型別，或者根據型別篩選集合。  
  
 DBQueryCommandTree.Query 屬性是描述查詢邏輯之運算式樹狀架構的根。  DBQueryCommandTree.Parameters 屬性包含用於查詢的參數清單。  由 DbExpression 物件所組成的運算式。  
  
 DbExpression 物件代表某些計算。  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會提供幾種運算式來撰寫查詢運算式，包括常數、變數、函式、建構函式，以及標準關係運算子 \(如 Filter 和 Join\)。  每一個 DbExpression 物件都有 ResultType 屬性，此屬性代表該運算式所產生之結果的型別。  這個型別會表示為 TypeUsage。  
  
## 輸出查詢命令樹的形狀  
 輸出查詢命令樹緊密地代表關聯式 \(SQL\) 查詢，而且與查詢命令樹所套用的規則相較之下，前者會遵守更為嚴格的規則。  這些通常包含可輕鬆轉譯為 SQL 的建構。  
  
 輸入命令樹會針對概念模型來表示，概念模型可支援導覽屬性、多個實體之間的關聯及繼承。  輸出命令樹會針對儲存體模型來表示。  輸入命令樹可讓您投射巢狀集合，但輸出命令樹則不行。  
  
 輸出查詢命令樹是使用可用的 DbExpression 物件子集所建置，而且即使是該子集中的某些運算式也是有使用上的限制。  
  
 型別作業 \(就像檢查給定運算式是否具有特定型別，或是根據型別篩選集合\) 不會出現在輸出命令樹中。  
  
 在輸出命令樹中，只有傳回布林值的運算式會用於投射，而且只適用於需要述詞 \(如 filter 或 case 陳述式\) 之運算式中的述詞。  
  
 輸出查詢命令樹的根為 DbProjectExpression 物件。  
  
### 輸出查詢命令樹中未出現運算式型別  
 下列運算式型別在輸出查詢命令樹中無效，而且不需要由提供者來處理：  
  
 DbDerefExpression  
  
 DbEntityRefExpression  
  
 DbRefKeyExpression  
  
 DbIsOfExpression  
  
 DbOfTypeExpression  
  
 DbRefExpression  
  
 DbRelationshipNavigationExpression  
  
 DbTreatExpression  
  
### 運算式限制和備註  
 許多運算式在輸出查詢命令樹中，只能以限制的方式來使用：  
  
#### DbFunctionExpression  
 下列是可以傳遞的函式型別：  
  
-   Edm 命名空間所辨識的標準函式。  
  
-   BuiltInAttribute 所辨識的內建 \(存放區\) 函式。  
  
-   使用者定義函式。  
  
 標準函式 \(詳細資訊請參閱[標準函式](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)\) 會當做 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的一部分來指定，而且提供者應該根據這些規格，為標準函式提供實作。  存放區函式是根據對應之提供者資訊清單中的規格。  使用者定義函式是根據 SSDL 中的規格。  
  
 此外，具有 NiladicFunction 屬性的函式沒有任何引數，而且轉譯時結尾不應該有括號。  也就是轉譯成 *\<functionName\>*，而不是 *\<functionName\>\(\)*。  
  
#### DbNewInstanceExpression  
 DbNewInstanceExpression 只能發生在下列兩個案例中：  
  
-   當做 DbProjectExpression 的 Projection 屬性。  當依照這類情況使用時，要遵守下列限制：  
  
    -   結果型別必須是資料列型別。  
  
    -   它的每一個引數都是一個運算式，可產生具有基本型別的結果。  一般來說，每一個引數都是純量運算式，例如透過 DbVariableReferenceExpression 的 PropertyExpression、函式引動過程，或是透過 DbVariableReferenceExpression 或函式引動過程之 DbPropertyExpression 的算術運算。  但是，代表純量子查詢的運算式也可以出現在 DbNewInstanceExpression 的引數清單中。  代表純量子查詢的運算式是代表子查詢的一種運算式樹狀架構，可恰好傳回基本型別的一個資料列和一個資料行，而且包含 DbElementExperession 物件根。  
  
-   有了集合傳回型別，就可以定義當做引數提供之運算式的新集合。  
  
#### DbVariableReferenceExpression  
 DbVariableReferenceExpression 必須是 DbPropertyExpression 節點的子系。  
  
#### DbGroupByExpression  
 DbGroupByExpression 的 Aggregates 屬性只能擁有 DbFunctionAggregate 型別的項目。  沒有其他任何彙總型別。  
  
#### DbLimitExpression  
 屬性限制只能是 DbConstantExpression 或 DbParameterReferenceExpression。  此外，WithTies 屬性在 .NET Framework 3.5 版中一定是 false。  
  
#### DbScanExpression  
 當用於輸出命令樹時，DbScanExpression 會有效地代表對資料表、檢視表或存放區查詢的掃描 \(以 EnitySetBase::Target 表示\)。  
  
 如果目標的中繼資料屬性 “Defining Query” 不是 null，則它會代表查詢，該查詢的查詢文字會在提供者專用語言 \(或方言\) 的中繼資料屬性中提供，如同存放結構定義中所指定。  
  
 否則，目標會代表資料表或檢視表。  它的結構描述前置詞不是位於 “Schema” 中繼資料屬性中 \(如果不是 null\)，就是實體容器名稱。  資料表或檢視表名稱不是 “Table” 中繼資料屬性 \(如果不是 null\)，就是實體集基底的 Name 屬性。  
  
 所有的這些屬性都來自於存放結構定義檔案 \(SSDL\) 中對應 EntitySet 的定義。  
  
### 使用基本型別  
 在輸出命令樹中參考基本型別時，通常會在概念模型的基本型別中參考這些型別。  但是對於某些運算式而言，提供者需要對應的存放區基本型別。  這類運算式的範例包括 DbCastExpression，也可能包括 DbNullExpression \(如果提供者需要將 null 轉型為對應的型別\)。  在這些情況下，提供者應該根據基本型別種類和它的 Facet，執行與提供者型別的對應。  
  
## 請參閱  
 [SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)