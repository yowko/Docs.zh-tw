---
title: 架構與設計
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: a4b597c8a62c661ace4485959589823094b9a08f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307570"
---
# <a name="architecture-and-design"></a>架構與設計
中的 SQL 產生模組[範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)會實作成運算式樹狀架構表示的命令樹上的造訪者。 此產生作業是透過運算式樹狀結構，在單一行程中完成。  
  
 樹狀結構節點的處理方式是由下而上。 首先，會產生中繼結構：: SqlSelectStatement 或 SqlBuilder，這兩個實作 ISqlFragment。 接著，系統會根據該結構產生 SQL 陳述式字串。 使用中繼結構的原因有兩個：  
  
-   就邏輯上來說，SQL SELECT 陳述式會以不按照順序的方式擴展。 系統會先造訪參與 FROM 子句的節點，然後再造訪參與 WHERE、GROUP BY 和 ORDER BY 子句的節點。  
  
-   若要重新命名別名，您必須識別所有使用的別名，才能避免在重新命名期間發生衝突。 若要在 SqlBuilder 中延後重新命名選擇，請使用 Symbol 物件來代表成為重新命名候選的資料行。  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 在第一個階段中，造訪運算式樹狀時，運算式會組成 SqlSelectStatement、聯結會扁平化，而且聯結別名也會扁平化。 在這個行程中，Symbol 物件代表可重新命名的資料行或輸入別名。  
  
 在第二個階段中，產生實際字串時，就會重新命名別名。  
  
## <a name="data-structures"></a>資料結構  
 本章節將討論使用中的型別[範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)您用於建立 SQL 陳述式。  
  
### <a name="isqlfragment"></a>ISqlFragment  
 本節內容涵蓋了實作 ISqlFragment 介面的類別，而這個介面具有兩種用途：  
  
-   當做所有造訪者方法的一般傳回型別。  
  
-   提供寫入最終 SQL 字串的方法。  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder 是一種最終 SQL 字串的蒐集裝置，與 StringBuilder 很相似。 它包含了組成最終 SQL 的字串，以及可轉換成字串的 ISqlFragment。  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 SqlSelectStatement 代表標準 SQL SELECT 陳述式的圖形"SELECT... 從... WHERE... 分組依據... ORDER BY。 」  
  
 其中每個 SQL 子句都由 StringBuilder 表示。 此外，它會追蹤是否已經指定 Distinct 以及此陳述式是否為最上層。 如果此陳述式不是最上層，除非此陳述式也具有 TOP 子句，否則就會省略 ORDER BY 子句。  
  
 FromExtents 包含 SELECT 陳述式的輸入清單。 不過，這個清單通常只有一個項目。 聯結的 SELECT 陳述式可能會暫時具有多個項目。  
  
 如果 SELECT 陳述式是由聯結節點所建立，SqlSelectStatement 就會維護已經在 AllJoinExtents 之聯結中扁平化的所有範圍清單。 OuterExtents 代表 SqlSelectStatement 的外部參考，用於輸入別名重新命名。  
  
```  
internal sealed class SqlSelectStatement : ISqlFragment {  
   internal bool IsDistinct { get, set };  
   internal bool IsTopMost  
  
   internal List<Symbol> AllJoinExtents { get, set };  
   internal List<Symbol> FromExtents { get};  
   internal Dictionary<Symbol, bool> OuterExtents { get};  
  
   internal TopClause Top { get, set };  
  
   internal SqlBuilder Select {get};  
   internal SqlBuilder From  
   internal SqlBuilder Where  
   internal SqlBuilder GroupBy  
   public SqlBuilder OrderBy  
}  
```  
  
#### <a name="topclause"></a>TopClause  
 TopClause 代表 SqlSelectStatement 中的 TOP 運算式。 TopCount 屬性會指出應該選取多少個 TOP 資料列。  當 WithTies 為 true 時，就會根據 DbLimitExpession 建置 TopClause。  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>符號  
 Symbol 相關類別和符號表會執行輸入別名重新命名、聯結別名扁平化和資料行別名重新命名。  
  
 Symbol 類別代表範圍、巢狀 SELECT 陳述式或資料行。 它會用來取代實際別名，以便在使用此類別之後允許重新命名，而且也帶有它所代表之成品的其他資訊 (例如型別)。  
  
```  
class Symbol : ISqlFragment {  
   internal Dictionary<string, Symbol> Columns {get}  
   internal bool NeedsRenaming {get, set}  
   internal bool IsUnnest {get, set}   //not used  
  
   public string Name{get}  
   public string NewName {get,set}  
   internal TypeUsage Type {get, set}  
  
   public Symbol(string name, TypeUsage type)  
}  
```  
  
 Name 會儲存所代表之範圍、巢狀 SELECT 陳述式或資料行的原始別名。  
  
 NewName 會儲存將用於 SQL SELECT 陳述式的別名。 它原本設定為 Name，而且只有在產生最終字串查詢時，才會視需要重新命名。  
  
 Type 僅適用於代表範圍和巢狀 SELECT 陳述式的符號。  
  
#### <a name="symbolpair"></a>SymbolPair  
 SymbolPair 類別會處理記錄扁平化。  
  
 以屬性運算式 D(v, "j3.j2.j1.a.x") 為例，其中 v 是 VarRef、j1、j2 和 j3 是聯結、a 是範圍，而 x 是資料行。  
  
 這個運算式最後必須轉譯成 {j'}.{x'}。 Source 欄位代表最外層的 SqlStatement，而後者代表聯結運算式 (例如 j2)。這一定是聯結符號。 Column 欄位會從某個聯結符號移至下一個聯結符號，直到它停止於非聯結符號為止。 這個運算式會在造訪 DbPropertyExpression 時傳回，但是絕對不會加入至 SqlBuilder。  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 聯結符號是指代表具有聯結或聯結輸入之巢狀 SELECT 陳述式的符號。  
  
```  
internal sealed class JoinSymbol : Symbol {  
   internal List<Symbol> ColumnList {get, set}  
   internal List<Symbol> ExtentList {get}  
   internal List<Symbol> FlattenedExtentList {get, set}  
   internal Dictionary<string, Symbol> NameToExtent {get}  
   internal bool IsNestedJoin {get, set}  
  
   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)  
}  
```  
  
 如果這個符號代表 SQL SELECT 陳述式，ColumnList 就會代表 SELECT 子句中的資料行清單。 ExtentList 是指 SELECT 子句中的範圍清單。 如果此聯結具有多個在最上層扁平化的範圍，FlattenedExtentList 就會追蹤這些範圍，以便確保範圍別名正確重新命名。  
  
 NameToExtent 具有 ExtentList 中的所有範圍做為字典。 IsNestedJoin 是用來判斷 JoinSymbol 是一般聯結符號，還是具有對應 SqlSelectStatement 的聯結符號。  
  
 所有清單只會設定一次，然後再用於查閱或列舉。  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable 是用來將變數名稱解析成符號。 SymbolTable 會實作成堆疊，而且每個範圍都有新的項目。 查閱會從堆疊頂端搜尋到底部，直到找到項目為止。  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 SQL 產生模組的每個執行個體都只有一個 SymbolTable。 系統會針對每個關聯節點進入並退出範圍。 除非具有相同名稱的其他符號隱藏了範圍，否則先前範圍中的所有符號都會顯示給後續範圍查看。  
  
### <a name="global-state-for-the-visitor"></a>造訪者的全域狀態  
 若要協助重新命名別名和資料行，請維護已經透過查詢樹狀在第一個行程中使用的所有資料行名稱 (AllColumnNames) 和範圍別名 (AllExtentNames) 清單。  符號表會將變數名稱解析成符號。 IsVarRefSingle 僅用於驗證目的，並非絕對必要。  
  
 經由 CurrentSelectStatement 和 IsParentAJoin 使用的兩個堆疊會用來將「參數」從父節點傳遞至子節點，因為造訪者模式不允許我們傳遞參數。  
  
```  
internal Dictionary<string, int> AllExtentNames {get}  
internal Dictionary<string, int> AllColumnNames {get}  
SymbolTable symbolTable = new SymbolTable();  
bool isVarRefSingle = false;  
  
Stack<SqlSelectStatement> selectStatementStack;  
private SqlSelectStatement CurrentSelectStatement{get}  
  
Stack<bool> isParentAJoinStack;  
private bool IsParentAJoin{get}  
```  
  
## <a name="common-scenarios"></a>常見案例  
 本節將討論常見的提供者案例。  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>將運算式節點組成 SQL 陳述式  
 由下而上造訪樹狀時，如果遇到第一個關聯節點 (通常是 DbScanExpression 範圍)，就會建立 SqlSelectStatement。 若要產生巢狀查詢越少越好的 SQL SELECT 陳述式，請在該 SqlSelectStatement 中盡可能彙總其父節點 (越多越好)。  
  
 決定給定 (關聯) 節點是否能加入至目前的 SqlSelectStatement (造訪輸入時傳回) 或者是否需要啟動新的陳述式是由 IsCompatible 方法計算而得，而且主要取決於已經存在 SqlSelectStatement 中的項目 (根據哪些節點低於給定節點而定)。  
  
 一般而言，如果 SQL 陳述式子句是在考慮要合併之節點不是空的子句之後進行評估，此節點就無法加入至目前的陳述式。 例如，如果下一個節點是篩選，只有當下列條件成立時，該節點才能併入目前的 SqlSelectStatement：  
  
-   SELECT 清單是空的。 如果 SELECT 清單不是空的，就表示 SELECT 清單是由篩選前面的節點所產生，而且述詞可能會參考該 SELECT 清單所產生的資料行。  
  
-   GROUPBY 是空的。 如果 GROUPBY 不是空的，加入篩選就表示在分組之前篩選，而這是不正確的作法。  
  
-   TOP 子句是空的。 如果 TOP 子句不是空的，加入篩選就表示在進行 TOP 之前篩選，而這是不正確的作法。  
  
 這不會套用至 DbConstantExpression 或算術運算式等非關聯節點，因為這些節點一定會包含在現有的 SqlSelectStatement 中。  
  
 此外，遇到聯結樹狀結構的根 (沒有聯結父系的聯結節點) 時，就會啟動新的 SqlSelectStatement。 所有其左背面聯結子系都會彙總至該 SqlSelectStatement 中。  
  
 每當啟動新的 SqlSelectStatement，而且目前的陳述式已加入至輸入時，可能必須透過加入投影資料行 (SELECT 子句) 完成目前的 SqlSelectStatement (如果 SELECT 子句不存在的話)。 這項作業是使用 AddDefaultColumns 方法來完成，這個方法會查看 SqlSelectStatement 的 FromExtents 並將 FromExtents 所代表之範圍清單帶入範圍內的所有資料行加入至投影資料行清單。 完成這項作業的原因是，此時無法得知其他節點參考了哪些資料行。 這項作業可最佳化為僅投影之後可用的資料行。  
  
### <a name="join-flattening"></a>聯結扁平化  
 IsParentAJoin 屬性有助於判斷給定的聯結是否能夠扁平化。 尤其，IsParentAJoin 只會針對聯結的左子系以及屬於聯結之立即輸入的每個 DbScanExpression 傳回 `true`，而在此情況下，子節點會重複使用父系之後使用的相同 SqlSelectStatement。 如需詳細資訊，請參閱＜聯結運算式＞。  
  
### <a name="input-alias-redirecting"></a>輸入別名重新導向  
 輸入別名重新導向是使用符號表來達成。  
  
 若要說明輸入的別名重新導向，請參閱中的第一個範例[產生的 SQL，從命令樹-最佳作法](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)。  在該範例中，"a" 必須重新導向至投影中的 "b"。  
  
 建立 SqlSelectStatement 物件時，屬於節點之輸入的範圍就會放入 SqlSelectStatement 的 From 屬性。 符號 (< symbol_b >) 會根據輸入繫結名稱 ("b") 以表示該範圍而且"AS"+ < symbol_b > 會附加至 From 子句。  此符號也會加入至 FromExtents 屬性。  
  
 此符號也會加入至符號表，以便將輸入繫結名稱連結到它 （"b"，< symbol_b >） 中。  
  
 如果後續節點重複使用該 SqlSelectStatement，它就會在符號表中加入一個項目，以便將其輸入繫結名稱連結至該符號。 在本例中，輸入繫結名稱為"a"的 DbProjectExpression 會重複使用 SqlSelectStatement 並新增 ("a"、 \< symbol_b >) 的資料表。  
  
 當運算式參考正在重複使用 SqlSelectStatement 之節點的輸入繫結名稱時，就會使用符號表，將該參考解析成正確的重新導向符號。 "A"從"a.x"解析時同時造訪 DbVariableReferenceExpression 代表"a"it 會解析成符號 < symbol_b >。  
  
### <a name="join-alias-flattening"></a>聯結別名扁平化  
 聯結別名扁平化是在造訪 DbPropertyExpression 時達成，如＜DbPropertyExpression＞一節所述。  
  
### <a name="column-name-and-extent-alias-renaming"></a>資料行名稱和範圍別名重新命名  
 資料行名稱和範圍別名重新命名的問題所產生的 SQL 產生第二個階段一節中所述的第二個階段中使用別名的僅替代的符號：產生字串命令。  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>SQL 產生的第一個階段：瀏覽運算式樹狀架構  
 本節將描述 SQL 產生的第一個階段，這個階段會造訪代表查詢的運算式並且產生中繼結構：SqlSelectStatement 或 SqlBuilder。  
  
 本節將描述造訪不同運算式節點分類的原則，以及造訪特定運算式型別的詳細資料。  
  
### <a name="relational-non-join-nodes"></a>關聯 (非聯結) 節點  
 下列運算式型別支援非聯結節點：  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 造訪這些節點的作業會遵循下列模式：  
  
1. 造訪關聯輸入並取得產生的 SqlSelectStatement。 關聯節點的輸入可能是下列其中一項：  
  
    -   關聯節點，包括範圍 (例如 DbScanExpression)。 造訪這類節點會傳回 SqlSelectStatement。  
  
    -   設定作業運算式 (例如 UNION ALL)。 其結果必須用括弧包裝並且放入新 SqlSelectStatement 的 FROM 子句中。  
  
2. 檢查目前的節點是否能夠加入至輸入所產生的 SqlSelectStatement。 ＜將運算式組成 SQL 陳述式＞一節將詳細說明這點。 如果無法加入，則  
  
    -   推出目前的 SqlSelectStatement 物件。  
  
    -   建立新的 SqlSelectStatement 物件並加入推出的 SqlSelectStatement 做為新 SqlSelectStatement 物件的 FROM。  
  
    -   將新物件放在堆疊的頂端。  
  
3. 將輸入運算式繫結重新導向至輸入中的正確符號。 這項資訊會在 SqlSelectStatement 物件中維護。  
  
4. 加入新的 SymbolTable 範圍。  
  
5. 造訪運算式的非輸入部分 (例如投影和述詞)。  
  
6. 推出加入至全域堆疊的所有物件。  
  
 DbSkipExpression 沒有 SQL 的直接對等項目。 就邏輯上來說，它會轉譯成：  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>聯結運算式  
 下列運算式會被視為聯結運算式，而且它們是以常見的方式進行處理 (透過 VisitJoinExpression 方法)：  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 下面是造訪步驟：  
  
 第一步，造訪子系之前，系統會叫用 IsParentAJoin 來檢查聯結節點是否屬於左背面聯結的子系。 如果傳回 false，就會啟動新的 SqlSelectStatement。 就這個方面來看，聯結的造訪方式與其餘節點不同，因為父系 (聯結節點) 會針對可能要使用的子系建立 SqlSelectStatement。  
  
 第二步，一次處理一個輸入。 針對每個輸入：  
  
1. 造訪輸入。  
  
2. 透過叫用 ProcessJoinInputResult，後置處理造訪輸入的結果，而這個方法會在造訪聯結運算式的子系以及可能完成子系所產生的 SqlSelectStatement 之後負責維護符號表。 子系的結果可能是下列其中一項：  
  
    -   與即將加入父系之陳述式不同的 SqlSelectStatement。 在這種情況下，它可能必須透過加入預設資料行完成。 如果輸入是聯結，您就必須建立新的聯結符號。 否則，請建立一般符號。  
  
    -   範圍 (例如 DbScanExpression)，在此情況下，它只會加入至父系之 SqlSelectStatement 的輸入清單。  
  
    -   非 SqlSelectStatement，在此情況下，它會用括弧包裝。  
  
    -   加入父系的相同 SqlSelectStatement。 在這種情況下，FromExtents 清單中的符號都必須取代成代表所有符號的單一新 JoinSymbol。  
  
    -   在前三種情況中，系統會呼叫 AddFromSymbol 來加入 AS 子句，並且更新符號表。  
  
 第三步，造訪聯結條件 (如果有的話)。  
  
### <a name="set-operations"></a>設定作業  
 設定作業 DbUnionAllExpression、DbExceptExpression 和 DbIntersectExpression 是由 VisitSetOpExpression 方法所產生。 這個方法會建立 SqlBuilder，其形狀為：  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 其中\<leftSqlSelectStatement > 並\<rightSqlSelectStatement > 會造訪每個輸入，取得的 Sqlselectstatement 並\<setOp > 是對應的作業 (例如 UNION ALL)。  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 如果在聯結內容中造訪 (當做屬於另一個聯結左子系之聯結的輸入)，DbScanExpression 就會傳回 SqlBuilder 並將目標 SQL 設定為對應的目標 (定義查詢、資料表或檢視表)。 否則，就會建立新的 SqlSelectStatement 並將 FROM 欄位設定為對應至對應的目標。  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 造訪 DbVariableReferenceExpression 會根據符號表中的查閱，傳回對應至該變數參考運算式的符號。  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 聯結別名扁平化是在造訪 DbPropertyExpression 時識別並處理。  
  
 系統會先造訪 Instance 屬性，而且其結果為 Symbol、JoinSymbol 或 SymbolPair。 下面是這三種情況的處理方式：  
  
-   如果傳回了 JoinSymbol，則其 NameToExtent 屬性會包含代表所需屬性的符號。 如果此聯結符號代表巢狀聯結，就會傳回具有聯結符號的新符號配對，以便追蹤當做執行個體別名使用的符號，以及代表要進一步解析之實際屬性的符號。  
  
-   如果傳回了 SymbolPair 而且 Column 部分是聯結符號，就會再次傳回聯結符號，但是這次 Column 屬性會更新為指向目前屬性運算式所代表的屬性。 否則，就會傳回 SqlBuilder，並將 SymbolPair 來源當做別名，而將目前屬性的符號當做資料行。  
  
-   如果傳回了 Symbol，Visit 方法就會傳回 SqlBuilder 方法，並將該執行個體當做別名，而將屬性名稱當做資料行名稱。  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 將 DbNewInstanceExpression 當做 DbProjectExpression 的 Projection 屬性使用時，它會產生引數的逗號分隔清單，代表投影的資料行。  
  
 當 DbNewInstanceExpression 具有集合傳回型別，而且定義當做引數提供之運算式的新集合時，就會個別處理下列三種情況：  
  
-   如果 DbNewInstanceExpression 具有 DbElementExpression 當做唯一的引數，它就會轉譯成：  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 如果 DbNewInstanceExpression 沒有任何引數 (代表空的資料表)，DbNewInstanceExpression 就會轉譯成：  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 否則，DbNewInstanceExpression 就會建置引數的 UNION ALL 階梯：  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 標準函式與內建函式的處理方式都相同：如果它們需要特殊處理 (例如 TRIM(string) 到  LTRIM(RTRIM(string))，就會叫用適當的處理常式。 否則，它們會轉譯成 FunctionName(arg1, arg2, ..., argn)。  
  
 字典是用來追蹤哪些函式需要特殊處理及其適當的處理常式。  
  
 使用者定義函式會轉譯成 NamespaceName.FunctionName(arg1, arg2, ..., argn)。  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 造訪 DbElementExpression 的方法只會針對造訪用來代表純量子查詢的 DbElementExpression 叫用。 因此，DbElementExpression 會轉譯成完整的 SqlSelectStatement 並在前後加上括弧。  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 根據運算式型別 (Any 或 All)，DbQuantifierExpression 會轉譯成：  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>DbNotExpression  
 在某些情況下，您可以使用 DbNotExpression 的輸入運算式來摺疊其轉譯。 例如：  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 執行第二次摺疊的原因是，轉譯型別為 All 的 DbQuantifierExpression 時，提供者會發生效率不佳的情況。 因此，Entity Framework 無法完成簡化。  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression 會轉譯成：  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL 產生的第二個階段：產生字串命令  
 產生字串 SQL 命令時，SqlSelectStatement 會產生符號的實際別名，以便處理資料行名稱和範圍別名重新命名的問題。  
  
 範圍別名重新命名是在將 SqlSelectStatement 物件寫入字串時進行。 先建立外部範圍所使用之所有別名的清單。 FromExtents (或 AllJoinExtents，如果它是非 null 的話) 中的每個符號都會重新命名 (如果它與任何外部範圍發生衝突的話)。 如果需要重新命名，它就不會與 AllExtentNames 中收集的任何範圍發生衝突。  
  
 資料行重新命名是在將 Symbol 物件寫入字串時進行。 在第一個階段中，AddDefaultColumns 已經判斷出特定資料行符號是否必須重新命名。 在第二個階段中，只會進行重新命名作業，確保產生的名稱不會與 AllColumnNames 中使用的任何名稱發生衝突。  
  
 若要產生唯一的名稱，同時針對範圍別名與資料行，請使用 < existing_name > _n 其中 n 是尚未使用的最小別名。 所有別名的全域清單會增加串聯重新命名的需求。  
  
## <a name="see-also"></a>另請參閱

- [範例提供者中的 SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
