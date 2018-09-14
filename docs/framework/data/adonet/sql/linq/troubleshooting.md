---
title: 疑難排解
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 6fe4f789ca64c0646b77fdb66b0c6e2b73763293
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509970"
---
# <a name="troubleshooting"></a>疑難排解
下列資訊將說明一些您在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中可能會遇到的問題，並提供建議來避免或降低這些問題的影響。  
  
 其他問題的解答[常見問題集](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)。  
  
## <a name="unsupported-standard-query-operators"></a>不支援的標準查詢運算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 並非支援所有標準查詢運算子方法 (例如 <xref:System.Linq.Enumerable.ElementAt%2A>)。 因此，專案即使可以編譯，仍可能產生執行階段錯誤。 如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)。  
  
## <a name="memory-issues"></a>記憶體問題  
 如果查詢牽涉到記憶體中集合和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>，可能會在記憶體中，根據在其中指定兩個集合的順序執行查詢。 如果查詢必須在記憶體中執行，則必須擷取資料庫資料表中的資料。  
  
 這種方式沒有效率，而且可能會耗用大量的記憶體和處理器資源。 請盡量避免這種多重定義域查詢。  
  
## <a name="file-names-and-sqlmetal"></a>檔案名稱和 SQLMetal  
 若要指定輸入檔案名稱，請將名稱以輸入檔案加入命令列。 不支援將檔案名稱包含在連接字串中 (使用 **/conn** 選項)。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="class-library-projects"></a>類別庫專案  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]會在專案的 `app.config` 檔案中建立連接字串。 類別庫專案不使用 `app.config` 檔案。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用設計階段檔案中提供的連接字串。 變更 `app.config` 中的值不會變更應用程式所連接的資料庫。  
  
## <a name="cascade-delete"></a>串聯刪除  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援或辨識串聯 (Cascade) 刪除作業。 如果您要刪除有條件約束之資料表中的資料列，必須執行下列其中一項工作：  
  
-   在資料庫的外部索引鍵條件約束中設定 `ON DELETE CASCADE` 規則。  
  
-   使用您自己的程式碼，先刪除使父物件無法刪除的子物件。  
  
 否則會擲回 <xref:System.Data.SqlClient.SqlException> 例外狀況。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 刪除資料列從資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。  
  
## <a name="expression-not-queryable"></a>無法查詢運算式  
 如果您看到「運算式 [expression] 無法查詢；是否遺漏組件參考？」 錯誤，請確定下列各項：  
  
-   應用程式的目標為 [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)]。  
  
-   您有 `System.Core.dll` 和 `System.Data.Linq.dll` 的參考。  
  
-   您必須`Imports`(Visual Basic) 或`using`(C#) 指示詞<xref:System.Linq>和<xref:System.Data.Linq>。  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 在偵錯[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]專案中，您可能會周遊某個實體的關聯。 如此一來帶入快取中，這些項目和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]察覺到它們的存在。 如果您接著嘗試執行 <xref:System.Data.Linq.Table%601.Attach%2A> 或 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>，或是類似方法來產生有相同索引鍵的多個資料列，就會擲回 <xref:System.Data.Linq.DuplicateKeyException>。  
  
## <a name="string-concatenation-exceptions"></a>字串串連例外狀況  
 串連對應到 `[n]text` 和其他 `[n][var]char` 的運算元是不支援的做法。 串連對應到兩組不同型別的字串時，會擲回例外狀況。 如需詳細資訊，請參閱 < [System.String 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)。  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>SQL Server 2000 中的 Skip 和 Take 例外狀況  
 當您對 SQL Server 2000 資料庫使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 或 <xref:System.Linq.Queryable.Take%2A> 時，必須使用識別成員 (<xref:System.Linq.Queryable.Skip%2A>)。 此查詢必須針對單一資資料表 (即非聯結資料表) 執行，或為 <xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A> 或 <xref:System.Linq.Queryable.Union%2A> 作業，而且不能包含 <xref:System.Linq.Queryable.Concat%2A> 作業。 如需詳細資訊，請參閱中的 < SQL Server 2000 支援 > 一節[標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)。  
  
 這項需求不適用於 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]。  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 當以 <xref:System.Linq.Enumerable.GroupBy%2A> 運算式做為群組依據 (例如 `boolean`) 的 `group x by (Phone==@phone)` 查詢有資料行的值為 null 時，會擲回此例外狀況。 由於運算式為 `boolean`，因此會推斷索引鍵也為 `boolean`，而非 `nullable` `boolean`。 當轉譯後的比較產生 null 時，若嘗試指派 `nullable` `boolean` 給 `boolean`，就會擲回此例外狀況。  
  
 為避免這個情況 (假設您要將 null 視為 false)，請使用類似下列的方式：  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated() 部分方法  
 每次呼叫物件建構函式時，都會呼叫產生的方法 `OnCreated()`，包括 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 呼叫建構函式來複製原始值的情況。 如果您要在自己的部分類別中實作 `OnCreated()` 方法，請將此行為列入考量。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [常見問題集](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
