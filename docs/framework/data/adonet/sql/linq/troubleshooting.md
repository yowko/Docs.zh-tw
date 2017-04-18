---
title: "疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 疑難排解
下列資訊將說明一些您在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中可能會遇到的問題，並提供建議來避免或降低這些問題的影響。  
  
 其他問題的解答則在[常見問題集](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md) 中。  
  
## 不支援的標準查詢運算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 並非支援所有標準查詢運算子方法 \(例如 <xref:System.Linq.Enumerable.ElementAt%2A>\)。  因此，專案即使可以編譯，仍可能產生執行階段錯誤。  如需詳細資訊，請參閱[標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)。  
  
## 記憶體問題  
 如果查詢牽涉到記憶體中的集合和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>，則查詢可能會在記憶體中執行，這會視指定這兩個集合的順序而定。  如果查詢必須在記憶體中執行，則必須擷取資料庫資料表中的資料。  
  
 這種方式沒有效率，而且可能會耗用大量的記憶體和處理器資源。  請盡量避免這種多重定義域查詢。  
  
## 檔案名稱和 SQLMetal  
 若要指定輸入檔案名稱，請將名稱以輸入檔案加入命令列。  不支援將檔案名稱包含在連接字串中 \(使用 **\/conn** 選項\)。  如需詳細資訊，請參閱[SqlMetal.exe \(程式碼產生工具\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## 類別庫專案  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]會在專案的 `app.config` 檔案中建立連接字串。  類別庫專案不使用 `app.config` 檔案。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用設計階段檔案中提供的連接字串。  變更 `app.config` 中的值不會變更應用程式所連接的資料庫。  
  
## 串聯刪除  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援或辨識串聯 \(Cascade\) 刪除作業。  如果您要刪除有條件約束之資料表中的資料列，必須執行下列其中一項工作：  
  
-   在資料庫的外部索引鍵條件約束中設定 `ON DELETE CASCADE` 規則。  
  
-   使用您自己的程式碼，先刪除使父物件無法刪除的子物件。  
  
 否則會擲回 <xref:System.Data.SqlClient.SqlException> 例外狀況。  
  
 如需詳細資訊，請參閱[HOW TO：從資料庫刪除資料列](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。  
  
## 無法查詢運算式  
 如果您看到「運算式 \[expression\] 無法查詢；是否遺漏組件參考？」錯誤，請確定下列事項：  
  
-   應用程式的目標為 [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)]。  
  
-   您有 `System.Core.dll` 和 `System.Data.Linq.dll` 的參考。  
  
-   <xref:System.Linq> 和 <xref:System.Data.Linq> 有 `Imports` \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) 或 `using` \(C\#\) 指示詞。  
  
## DuplicateKeyException  
 在偵錯 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案時，您可能會周遊某個實體的關聯。  這麼做會將這些項目快取起來，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就得知這些項目的存在。  如果您接著嘗試執行 <xref:System.Data.Linq.Table%601.Attach%2A> 或 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>，或是類似方法來產生有相同索引鍵的多個資料列，就會擲回 <xref:System.Data.Linq.DuplicateKeyException>。  
  
## 字串串連例外狀況  
 串連對應到 `[n]text` 和其他 `[n][var]char` 的運算元是不支援的做法。  串連對應到兩組不同型別的字串時，會擲回例外狀況。  如需詳細資訊，請參閱[System.String 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)。  
  
## SQL Server 2000 中的 Skip 和 Take 例外狀況  
 當您對 SQL Server 2000 資料庫使用 <xref:System.Linq.Queryable.Take%2A> 或 <xref:System.Linq.Queryable.Skip%2A> 時，必須使用識別成員 \(<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>\)。  此查詢必須針對單一資資料表 \(即非聯結資料表\) 執行，或為 <xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A> 或 <xref:System.Linq.Queryable.Union%2A> 作業，而且不能包含 <xref:System.Linq.Queryable.Concat%2A> 作業。  如需詳細資訊，請參閱[標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md) 中的＜SQL Server 2000 支援＞一節。  
  
 這項需求不適用於 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]。  
  
## GroupBy InvalidOperationException  
 當以 `boolean` 運算式做為群組依據 \(例如 `group x by (Phone==@phone)`\) 的 <xref:System.Linq.Enumerable.GroupBy%2A> 查詢有資料行的值為 null 時，會擲回此例外狀況。  由於運算式為 `boolean`，因此會推斷索引鍵也為 `boolean`，而非 `nullable` `boolean`。  當轉譯後的比較產生 null 時，若嘗試指派 `nullable` `boolean` 給 `boolean`，就會擲回此例外狀況。  
  
 為避免這個情況 \(假設您要將 null 視為 false\)，請使用類似下列的方式：  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## OnCreated\(\) 部分方法  
 每次呼叫物件建構函式時，都會呼叫產生的方法 `OnCreated()`，包括 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 呼叫建構函式來複製原始值的情況。  如果您要在自己的部分類別中實作 `OnCreated()` 方法，請將此行為列入考量。  
  
## 請參閱  
 [偵錯支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)   
 [常見問題集](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)