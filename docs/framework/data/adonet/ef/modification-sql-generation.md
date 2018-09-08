---
title: 修改 SQL 產生
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184937"
---
# <a name="modification-sql-generation"></a>修改 SQL 產生
本節將討論如何為您的 (SQL:1999 相容資料庫) 提供者開發修改 SQL 產生模組。 這個模組負責將修改命令樹轉譯為適當的 SQL INSERT、UPDATE 或 DELETE 陳述式。  
  
 如需 select 陳述式的 SQL 產生的資訊，請參閱[SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)。  
  
## <a name="overview-of-modification-command-trees"></a>修改命令樹概觀  
 修改 SQL 產生模組會根據給定輸入 DbModificationCommandTree 來產生資料庫特有的修改 SQL 陳述式。  
  
 DbModificationCommandTree 是修改 DML 作業 (插入、更新或刪除作業) 的物件模型表示法，繼承自 DbCommandTree。 DbModificationCommandTree 有三個實作：  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree 及其實作所產生的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]永遠都代表單一資料列作業。 這一節會描述 .NET Framework 3.5 版中的這些型別以及其條件約束。  
  
 ![圖表](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree 有一個目標屬性，此屬性代表針對修改作業設定的目標。 定義輸入集的目標運算式屬性一定是 DbScanExpression。  DbScanExpression 可以是會代表資料表或檢視，或一組資料使用查詢定義如果中繼資料屬性"Defining Query"其目標為非 null。  
  
 只有當集合是使用模型中的定義查詢所定義，但是未針對對應的修改作業提供任何功能時，代表查詢的 DbScanExpression 才能當做修改目標聯繫提供者。 提供者可能無法支援這種案例 (例如 SqlClient 就無法支援)。  
  
 DbInsertCommandTree 代表以命令樹表示的單一資料列插入作業。  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree 代表以命令樹表示的單一資料列更新作業。  
  
 DbDeleteCommandTree 代表以命令樹表示的單一資料列刪除作業。  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>修改命令樹屬性的限制  
 下列資訊和限制會套用到修改命令樹屬性。  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree 和 DbUpdateCommandTree 中的 Returning  
 當不是 null 時，Returning 表示命令會傳回讀取器。 否則，此命令應該會傳回純量值，表示受影響 (插入或更新) 的資料列數。  
  
 Returning 值會根據插入或更新的資料列，指定要傳回的結果投影。 它的型別只能是代表資料列的 DbNewInstanceExpression，而它的每一個引數都是透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。 用於 Returning 屬性之 DbPropertyExpressions 所代表的屬性一定會是存放區所產生或計算的值。 在 DbInsertCommandTree 中，當至少有一個資料表屬性 (資料列插入之處) 指定為存放區所產生或計算時 (標示為 ssdl 中的 StoreGeneratedPattern.Identity 或 StoreGeneratedPattern.Computed)，Returning 不會是 null。 在 DbUpdateCommandTrees 中，當至少有一個資料表屬性 (資料列更新之處) 指定為存放區所計算時 (標示為 ssdl 中的 StoreGeneratedPattern.Computed)，Returning 不會是 null。  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree 和 DbUpdateCommandTree 中的 SetClauses  
 SetClauses 會指定可定義插入或更新作業的插入或更新 SET 子句清單。  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Property 會指定應該更新的屬性。 它一定是透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。  
  
 Value 會指定用來更新屬性的新值。 它的型別會是 DbConstantExpression 或 DbNullExpression。  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>DbUpdateCommandTree 和 DbDeleteCommandTree 中的 Predicate  
 Predicate 會指定用來判斷所應該更新或刪除之目標集合成員的述詞。 它是從下列 DbExpressions 子集所建置的運算式樹狀架構：  
  
-   Equals 類型的 DbComparisonExpression，它的右邊子系是底下所限制的 DbPropertyExression，左邊子系則是 DbConstantExpression。  
  
-   DbConstantExpression  
  
-   透過 DbPropertyExpresison 的 DbIsNullExpression，如底下所限制  
  
-   透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。  
  
-   DbAndExpression  
  
-   DbNotExpression  
  
-   DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>範例提供者中的修改 SQL 產生  
 [Entity Framework 範例提供者](https://go.microsoft.com/fwlink/?LinkId=180616)之 ADO.NET 資料提供者支援的元件會示範[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 它會以 SQL Server 2005 資料庫為目標，並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者上層的包裝函式。  
  
 範例提供者的修改 SQL 產生模組 (位於 SQL Generation\DmlSqlGenerator.cs 檔案中) 會採用 DbModificationCommandTree 輸入，並產生單一修改 SQL 陳述式，後面可能接著 select 陳述式來傳回讀取器 (如果 DbModificationCommandTree 有指定)。 請注意，產生之命令的形狀會受到目標 SQL Server 資料庫所影響。  
  
### <a name="helper-classes-expressiontranslator"></a>協助程式類別：ExpressionTranslator  
 ExpressionTranslator 會當做 DbExpression 型別之所有修改命令樹屬性的常用輕量型轉譯程式。 它只支援修改命令樹屬性所限制之運算式型別的轉譯，而且會根據特定的條件約束來建置。  
  
 下列資訊將討論特定運算式型別的瀏覽 (略過具有一般轉譯的節點)。  
  
### <a name="dbcomparisonexpression"></a>DbComparisonExpression  
 當使用 preserveMemberValues = true 來建構 ExpressionTranslator 而且右邊的常數是 DbConstantExpression (而不是 DbNullExpression) 時，它會將左邊運算元 (DbPropertyExpressions) 與該 DbConstantExpression 產生關聯。 如果需要產生傳回 Select 陳述式來識別受影響的資料列，就會使用這個項目。  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 針對每一個瀏覽過的常數建立參數。  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 假設 DbPropertyExpression 的執行個體一定代表輸入資料表，則除非產生作業已經建立別名 (只發生在使用資料表變數時的更新案例中)，否則不需要為輸入指定別名。轉譯預設為屬性名稱。  
  
## <a name="generating-an-insert-sql-command"></a>產生插入 SQL 命令  
 如果範例提供者中有提供 DbInsertCommandTree，產生的插入命令會遵循底下的其中一個插入範本。  
  
 第一個範本有一個命令可在提供 SetClauses 清單中的值時執行插入，也有一個 SELECT 陳述式，可在 Returning 屬性不是 null 時，傳回 Returning 屬性中針對插入的資料列所指定的屬性。 述詞的項目 」\@ @ROWCOUNT > 0"為 true，如果已插入資料列。 述詞的項目"keyMemberI = keyValueI &#124; scope_identity （) 」 會在圖形"keyMemberI = scope_identity （）"才因為 scope_identity （） 會傳回插入識別 （最後一個識別值，只有當 keyMemeberI 為存放區所產生的金鑰，存放區所產生） 的資料行。  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 如果插入作業指定插入某個資料列 (這裡的主索引鍵為存放區所產生，但不是整數類型，所以不能搭配 scope_identity() 使用))，則需要第二個範本。 如果有存放區產生的複合索引鍵，也會使用它。  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 下列範例會使用範例提供者所隨附的模型。 它會從 DbInsertCommandTree 產生插入命令。  
  
 下列程式碼會插入分類：  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 此程式碼會產生傳遞給提供者的下列命令樹：  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 範例提供者產生的存放區命令為下列 SQL 陳述式：  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>產生更新 SQL 命令  
 如果有提供 DbUpdateCommandTree，產生的更新命令會根據下列範本：  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Set 子句具有假的 set 子句 ("@i = 0") 不指定任何 set 子句時，才。 這是為了確保任何存放區計算的資料行都會重新計算。  
  
 只有當 Returning 屬性不是 null 時，才會產生 select 陳述式來傳回 Returning 屬性中指定的屬性。  
  
 下列範例會使用範例提供者所隨附的模型來產生更新命令。  
  
 下列使用者程式碼會更新分類：  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 此使用者程式碼會產生傳遞給提供者的下列命令樹：  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 範例提供者會產生下列存放區命令：  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>產生刪除 SQL 命令  
 如果有提供 DbDeleteCommandTree，產生的 DELETE 命令會根據下列範本：  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 下列範例會使用範例提供者所隨附的模型來產生刪除命令。  
  
 下列使用者程式碼會刪除分類：  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 此使用者程式碼會產生傳遞給提供者的下列命令樹。  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 下列存放區命令是由範例提供者所產生：  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 Entity Framework 資料提供者](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
