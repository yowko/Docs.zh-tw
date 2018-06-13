---
title: SQL-CLR 類型不符
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 8b072c739b56d191e79b4cc2eff195adfe9da2eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365666"
---
# <a name="sql-clr-type-mismatches"></a>SQL-CLR 類型不符
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會自動執行物件模型 (Object Model) 與 SQL Server 之間大部分的轉譯作業。 不過，在某些情況下，還是無法進行精確的轉譯。 下列各節將摘要列出 Common Language Runtime (CLR) 型別與 SQL Server 資料庫型別之間的這些主要不符。 您可以找到更多特定的型別對應和在函式轉譯詳細[SQL CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)和[Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)。  
  
## <a name="data-types"></a>資料類型  
 CLR 與 SQL Server 之間的轉譯會在查詢傳送至資料庫，以及結果傳回給物件模型時進行。 例如，下列 Transact-SQL 查詢需要進行兩種值轉換：  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 您必須先指定 Transact-SQL 參數的值，然後才能在 SQL Server 上執行查詢。 在此範例中，`id` 參數值必須先從 CLR <xref:System.Int32?displayProperty=nameWithType> 型別轉譯成 SQL Server `INT` 型別，如此資料庫才能了解其值為何。 然後，為了擷取結果，SQL Server `DateOfBirth` 資料行必須從 SQL Server `DATETIME` 型別轉譯成 CLR <xref:System.DateTime?displayProperty=nameWithType> 型別，以便用於物件模型中。 在此範例中，CLR 物件模型與 SQL Server 資料庫中的型別都具有自然對應。 但是，這種情況不一定永遠成立。  
  
### <a name="missing-counterparts"></a>遺漏對應型別  
 下列型別沒有合理的對應型別。  
  
-   CLR <xref:System> 命名空間 (Namespace) 中的不符：  
  
    -   **不帶正負號的整數**。 這些型別通常會對應至大小較大且帶正負號的對應型別，以避免溢位。 常值可能會轉換為大小相同或較小的帶正負號數值 (以值為基礎)。  
  
    -   **布林**。 這些型別可以對應至一個位元或是較大的數值或字串。 常值可能會對應至評估為等值的運算式 (例如，SQL 中的 `1=1` 在 CLS 中為 `True`)。  
  
    -   **TimeSpan**。 這種型別代表兩個 `DateTime` 值之間的差異，而且不會對應至 SQL Server 的 `timestamp`。 在某些情況下，CLR <xref:System.TimeSpan?displayProperty=nameWithType> 可能也會對應至 SQL Server `TIME` 型別。 SQL Server `TIME` 型別只能用於代表小於 24 小時的正值。 CLR <xref:System.TimeSpan> 具有較大的範圍。  
  
    > [!NOTE]
    >  SQL Server 特有[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)]中的型別<xref:System.Data.SqlTypes>不包含在這項比較。  
  
-   SQL Server 中的不符：  
  
    -   **固定長度字元型別**。 TRANSACT-SQL 會區分 Unicode 與非 Unicode 類別目錄和每個類別中有三種不同類型： 固定長度`nchar` / `char`，可變長度`nvarchar` / `varchar`，和較大大小`ntext` / `text`。 固定長度字元型別可以對應至 CLR <xref:System.Char?displayProperty=nameWithType> 型別供字元擷取之用，但它們在轉換時和行為上並不會真的對應至這個型別。  
  
    -   **位元**。 雖然 `bit` 定義域與 `Nullable<Boolean>` 具有相同數目的值，但是它們是不同的型別。 `Bit` 會使用值`1`和`0`而不是`true` / `false`，而且無法當做布林運算式的對等用法。  
  
    -   **時間戳記**。 與 CLR <xref:System.TimeSpan?displayProperty=nameWithType> 型別不同的是，SQL Server `TIMESTAMP` 型別代表資料庫針對每次更新所產生的 8 位元組唯一數字，因此不是根據 <xref:System.DateTime> 值之間的差異。  
  
    -   **Money**和**SmallMoney**。 這些型別可以對應至 <xref:System.Decimal>，但是它們基本上是不同的型別，而且伺服器架構函式和轉換也會將它們視為不同的型別。  
  
### <a name="multiple-mappings"></a>多重對應  
 可對應至一或多個 CLR 資料型別的 SQL Server 資料型別有許多種。 可對應至一或多個 SQL Server 資料型別的 CLR 型別也有許多種。 雖然 LINQ to SQL 可能會支援某種對應，但是這並不表示在 CLR 與 SQL Server 之間對應的兩種型別在精確度、範圍和語意 (Semantics) 方面就是完美的相符。 在任何或所有這些維度 (Dimension) 中，某些對應可能會包含差異。 您可以找到有關這些潛在的差異的詳細資料的各種對應可能性在[SQL CLR 型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
### <a name="user-defined-types"></a>使用者定義型別  
 使用者定義 CLR 型別的設計目的是協助填補型別系統之間的差距。 不過，它們也產生型別版本控制的相關問題。 用戶端上的版本變更可能會與資料庫伺服器上儲存的型別變更不符。 任何這類變更都會導致另一項類型不符問題，即型別語意不相符，因而產生版本差距。 隨著後續版本重新調整繼承階層架構 (Inheritance Hierarchy)，情況會越來越複雜。  
  
## <a name="expression-semantics"></a>運算式語意  
 除了 CLR 與資料庫型別之間的配對錯誤以外，運算式也會使得不相符的情況更複雜。 運算子語意、函式語意、隱含型別轉換和優先順序規則中的不符處都必須納入考慮。  
  
 下列各副小節說明看似相似運算式之間的不符處。 雖然可以產生在語意上與某個 CLR 運算式相等的 SQL 運算式， 但是 CLR 使用者不一定能清楚看出看似相似運算式之間的語意差異，因此也就不知道語意對等關係的變更是不是必要。 在評估運算式來產生一組值時，這個問題特別重要。 差異是否明顯可能要視資料而定，而且可能很難在編碼和偵錯期間就識別出差異。  
  
### <a name="null-semantics"></a>Null 語意  
 SQL 運算式為布林值運算式提供三種邏輯值。 結果可以是 true、false 或 null。 另一方面，CLR 只會針對牽涉到 null 值的比較，指定兩種布林值結果。 請考慮下列程式碼：  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 採用兩種值的結果時可能會發生類似問題。  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 在上一個案例中，雖然產生的 SQL 會有對等的行為，但是轉譯作業可能不會精確地反映您的意圖。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會強制 C#`null`或 Visual Basic`nothing`在 SQL 上的比較語意。 比較運算子會轉譯為語法上的 SQL 對等用法。 而語意會反映伺服器所定義的 SQL 語意或連接設定。 在預設 SQL Server 設定下，兩個 null 值會視為不相等的值 (雖然您可以變更設定來變更語意)。 不過，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在轉譯查詢時並不會考慮伺服器設定。  
  
 結果為常值 `null` (`nothing`) 的比較作業會轉譯為適當的 SQL 版本 (`is null` 或 `is not null`)。  
  
 定序 (Collation) 中的值 `null` (`nothing`) 是由 SQL Server 所定義，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會變更這個定序。  
  
### <a name="type-conversion-and-promotion"></a>型別轉換和提升  
 SQL 支援在運算式中使用一組豐富的隱含轉換。 C# 中的類似運算式則需要明確轉換 (Cast)。 例如：  
  
-   在 SQL 中不需要任何明確轉換 (Cast)，就可以比較 `Nvarchar` 和 `DateTime` 型別，在 C# 中則需要明確轉換 (Conversion)。  
  
-   在 SQL 中 `Decimal` 會隱含地轉換為 `DateTime`。 C# 則不允許隱含轉換。  
  
 同樣地，因為基礎的一組型別不同，所以 Transact-SQL 中的型別優先順序也會與 C# 中的型別優先順序不同。 事實上，優先順序清單之間並沒有明確的子集/超集關聯性 (Relationship)。 例如，將 `nvarchar` 與 `varchar` 比較會將 `varchar` 運算式隱含地轉換為 `nvarchar`。 CLR 不提供對等的提升作業。  
  
 在簡單案例中，這些差異會使得包含轉換的 CLR 運算式對於對應的 SQL 運算式而言是多餘的。 更重要的是，SQL 運算式的中繼結果可能會隱含地提升成在 C# l 中沒有精確對應型別的型別，反之亦然。 整體來說，這類運算式的測試、偵錯和驗證作業會對使用者造成沈重的負擔。  
  
### <a name="collation"></a>定序  
 Transact-SQL 支援以字元字串型別的附註形式進行明確定序。 這些定序會決定特定比較的有效性。 例如，如果比較具有不同明確定序的兩個資料行，則會發生錯誤。 使用較簡化的 CTS 字串型別就不會造成這類錯誤。 參考下列範例：  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 實際上，定序子項子句建立*限制型別*不是可替代。  
  
 同樣地，這些型別系統的排序次序也有顯著的差異。 這項差異會影響結果的排序。 所有 16 位元組上的 <xref:System.Guid> 都會依詞彙編篡順序來排序 (`IComparable()`)，而 T-SQL 會依下列順序比較 GUID：node(10-15)、clock-seq(8-9)、time-high(6-7)、time-mid(4-5)、time-low(0-3)。 在 SQL 7.0 中，這項排序作業會在 NT 產生的 GUID 具有這類八位元順序時執行。 這種方式可確保在相同節點叢集上產生的 GUID，會根據時間戳記連續出現。 這種方式同時也適用於建置索引 (「插入」現在變成「附加」，而不是隨機 IO)。 後來在 Windows 中，這個順序基於隱私權考量被打亂了，但是 SQL 還是必須維護相容性。 因應措施是使用<xref:System.Data.SqlTypes.SqlGuid>而不是<xref:System.Guid>。  
  
### <a name="operator-and-function-differences"></a>運算子和函式差異  
 在本質上相等的運算子和函式，在語意上具有少許的差異。 例如：  
  
-   C# 會根據邏輯運算子 (Logical Operator) `&&` 和 `||` 的運算元語彙順序，指定最少運算 (Short Circuit) 語意。 相反地，SQL 是針對集合架構查詢，因此可提供更多的自由讓最佳化工具決定執行順序。 下列是部分隱含意義：  
  
    -   語意對等的轉譯，則必須"`CASE` ... `WHEN` … `THEN`「 SQL 以避免重設運算元執行順序中建構。  
  
    -   則鬆散轉譯為`AND` / `OR`運算子可能會導致未預期的錯誤，如果在 C# 運算式評估第二個運算元根據第一個運算元評估的結果。  
  
-   `Round()` 函式在 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 和 T-SQL 中的語意不同。  
  
-   在 CLR 中，字串的起始索引是 0，而在 SQL 中則是 1。 因此，任何具有索引的函式都需要進行索引轉譯。  
  
-   CLR 支援浮點數的模數 (‘%’) 運算子，而 SQL 則不支援。  
  
-   `Like` 運算子實際上會根據隱含轉換來取得自動多載。 雖然 `Like` 運算子是定義成對字元字串型別執行，但是將數值型別或 `DateTime` 型別等非字串型別進行隱含轉換後，同樣也可以使用 `Like`。 在 CTS 中，並沒有相等的隱含轉換。 因此，需要額外進行多載。  
  
    > [!NOTE]
    >  這個 `Like` 運算子行為僅適用於 C#，Visual Basic 的 `Like` 關鍵字仍未改變。  
  
-   溢位一定會先在 SQL 中檢查但有明確指定在 C# 中 （不在 Visual Basic) 若要避免發生繞回問題。 假設有三個整數資料行：C1、C2，和負責儲存 C1+C2 的 C3 (Update T Set C3 = C1 + C2)。  
  
    ```  
    create table T3 (  
        Col1      integer,  
        Col2      integer  
    )  
    insert into T3 (col1, col2) values (2147483647, 5)  
    -- Valid values: max integer value and 5.  
    select * from T3 where col1 + col2 < 0  
    -- Produces arithmetic overflow error.  
    ```  
  
 [!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
 [!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]  
  
-   SQL 會在 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 使用 Banker's Rounding (四捨六入五成雙) 時，執行對稱式算術捨入。 如需詳細資訊，請參閱知識庫文件 196652。  
  
-   根據預設，在通用地區設定 (Locale) 中，SQL 中的字元字串比較作業不會區分大小寫。 在 Visual Basic 和 C# 中，則會區分大小寫。 例如， `s == "Food"` (`s = "Food"`在 Visual Basic 中) 和`s == "Food"`可以產生不同的結果，如果`s`是`food`。  
  
    ```  
    -- Assume default US-English locale (case insensitive).  
    create table T4 (  
        Col1      nvarchar (256)  
    )  
    insert into T4 values (‘Food’)   
    insert into T4 values (‘FOOD’)  
    select * from T4 where Col1 = ‘food’  
    -- Both the rows are returned because of case-insensitive matching.  
    ```  
  
 [!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
 [!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]  
  
-   在 SQL 中套用至固定長度字元型別引數的運算子/函式，在語意上與套用至 CLR <xref:System.String?displayProperty=nameWithType> 的相同運算子/函式有顯著不同。 這也可以視為上面有關型別的一節中所討論之遺漏對應型別問題的延伸。  
  
    ```  
    create table T4 (  
        Col1      nchar(4)  
    )  
    Insert into T5(Col1) values ('21');  
    Insert into T5(Col1) values ('1021');  
    Select * from T5 where Col1 like '%1'  
    -- Only the second row with Col1 = '1021' is returned.  
    -- Not the first row!  
    ```  
  
     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]  
  
     將字串串連時也會發生類似問題。  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 總而言之，CLR 運算式可能需要進行迂迴的轉譯，而且可能需要有其他運算子/函式，才能公開SQL 功能。  
  
### <a name="type-casting"></a>型別轉換  
 在 C# 和 SQL 中，使用者可以使用明確型別轉換 (`Cast` 和 `Convert`) 來覆寫運算式的預設語意。 不過，是否跨型別系統界限公開這個功能，乃是一個兩難的選擇。 提供所需語意的 SQL 轉換 (Cast) 無法輕易地轉譯為對應的 C# 轉換 (Cast)。 另一方面，C# 轉換 (Cast) 也會因為類型不符、遺漏對應型別以及型別優先順序階層架構不同等問題，而無法直接轉譯為對等的 SQL 轉換 (Cast)。 因此，在公開型別系統不符處與損失運算式強大功能之間，需要有所取捨。  
  
 在其他情況下，這兩個定義域的運算式驗證作業可能都不需要進行型別轉換，但是也可能需要進行型別轉換以確保非預設對應已正確套用至運算式。  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a>效能問題  
 說明某些 SQL Server-CLR 型別差異可能會在 CLR 與 SQL Server 型別系統之間跨越時，造成效能降低。 影響效能之案例的範例包括：  
  
-   強制限制邏輯 and/or 運算子的評估順序  
  
-   如果產生的 SQL 會強制限制述詞的評估順序，SQL 最佳化工具的功能會無法發揮。  
  
-   型別轉換 (不論是透過 CLR 編譯器還是物件關聯式查詢實作進行) 可以減少索引的使用。  
  
     例如：  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     請考慮運算式 `(s = SOME_STRING_CONSTANT)` 的轉譯。  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 除了語意差異以外，請務必考量在 SQL Server 與 CLR 型別系統之間跨越時，對效能造成的影響。 如果是大型資料集，這類效能問題可能會決定部署應用程式的可行性。  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
