---
title: 一般結構描述集合
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 0b23164b56c6fefc6c258f313e9e17b156605518
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786792"
---
# <a name="common-schema-collections"></a>一般結構描述集合
通用結構描述集合是由每個 .NET Framework Managed 提供者所實作的結構描述集合。 您可以查詢 .NET Framework 的 managed 提供者，以判斷支援的架構集合清單，方法是呼叫不含引數的**GetSchema**方法，或使用架構集合名稱 "MetaDataCollections"。 這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。 這些集合會描述所有必要資料行。 如果願意，提供者可以隨意加入其他資料行。 例如，`SqlClient` 及 `OracleClient` 會將 ParameterName 加入限制集合。  
  
 如果提供者無法決定必要資料行的值，則會傳回 Null。  
  
 如需使用**GetSchema**方法的詳細資訊，請參閱[GetSchema 和架構集合](getschema-and-schema-collections.md)。  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 此結構描述集合會公開目前用於連接至資料庫之 .NET Framework Managed 提供者所支援的所有結構描述集合的相關資訊。  
  
|ColumnName|DataType|說明|  
|----------------|--------------|-----------------|  
|CollectionName|字串|要傳遞至**GetSchema**方法以傳回集合的集合名稱。|  
|NumberOfRestrictions|ssNoversion|可以為集合指定的限制數目。|  
|NumberOfIdentifierParts|ssNoversion|複合識別項/資料庫物件名稱的部分數目。 例如，在 SQL Server 中，資料表數目應為 3，資料行數目應為 4。 在 Oracle 中，資料表數目應為 2，資料行數目應為 3。|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 此結構描述集合會公開 .NET Framework Managed 提供者目前所連接之資料來源的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|字串|符合複合識別項中複合分隔符號的規則運算式。 例如，"\\." （適用于 SQL Server）或\@"&#124; \\." (適用於 Oracle)。<br /><br /> 複合識別碼通常是用於資料庫物件名稱的內容，例如： pubs. dbo. 作者或 pubs\@dbo. 作者。<br /><br /> 如 SQL Server，請使用正則運算式\\"."。 針對 OracleClient，請使用\@"&#124; \\."。<br /><br /> 若為 ODBC，請使用 Catalog_name_seperator。<br /><br /> 若為 OLE DB，請使用 DBLITERAL_CATALOG_SEPARATOR 或 DBLITERAL_SCHEMA_SEPARATOR。|  
|DataSourceProductName|字串|提供者存取的產品名稱，如 "Oracle" 或 "SQLServer"。|  
|DataSourceProductVersion|字串|表示提供者存取的產品版本，使用資料來源原生格式，而非 Microsoft 格式。<br /><br /> 在某些情況下，DataSourceProductVersion 及 DataSourceProductVersionNormalized 將為同一值。 若為 OLE DB 及 ODBC，這些值將永遠相同，因為它們對應於基礎原生 API 中的同一函式呼叫。|  
|DataSourceProductVersionNormalized|字串|資料來源的正規化版本，可使用 `String.Compare()` 進行比較。 它的格式對提供者的所有版本來說都一致，這可以防止版本 10 在版本 1 與版本 2 之間排序。<br /><br /> 例如，Oracle 提供者會針對其正規化版本使用 "nn. nn. nn" 格式，讓 Oracle 8i 資料來源傳回 "08.01.07.04.01"。 SQL Server 使用一般的 Microsoft "nn. nn. nnnn" 格式。<br /><br /> 在某些情況下，DataSourceProductVersion 及 DataSourceProductVersionNormalized 將為同一值。 若為 OLE DB 及 ODBC，這些值將永遠相同，因為它們對應於基礎原生 API 中的同一函式呼叫。|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|指定 GROUP BY 子句中的資料行與選取清單中的非彙總資料行的關係。|  
|IdentifierPattern|字串|符合識別項並具有識別項相符值的規則運算式。 例如 "[A-Za-z0-9_#$]"。|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|表示是否將非引號識別項視為區分大小寫。|  
|OrderByColumnsInSelect|bool|指定 ORDER BY 子句中的資料行是否必須包含於選取清單中。 True 值表示其必須包含於選取清單中，False 值表示其不必包含於選取清單中。|  
|ParameterMarkerFormat|字串|表示如何格式化參數的格式字串。<br /><br /> 如果資料來源支援具名參數，則此字串中的第一個替代符號位置應為要格式化參數名稱的位置。<br /><br /> 例如，如果資料來源預期參數要命名並以 '： ' 做為前置詞，則這會是 "{0}："。 使用參數名稱 "p1" 對進行格式化時，產生的字串為 ":p1"。<br /><br /> 如果資料來源預期參數前面會加上\@' '，但名稱中已包含，則這會是 '{0}'，而格式化名為 "\@p1" 的參數的結果會是 "\@p1"。<br /><br /> 對於不會預期具名引數的資料來源，並預期使用 '？ ' 字元，格式字串可以指定為單純的 '？ '，這會忽略參數名稱。 針對 OLE DB 將傳回 '?'。|  
|ParameterMarkerPattern|字串|符合參數標記的規則運算式。 它會具有參數名稱的相符值 (如果有的話)。<br /><br /> 例如，如果支援名稱為的參數，並將\@包含在參數名稱中的 ' ' 前置字元字元，則會是： "（\@[z0-9_ $ #] *）"。<br /><br /> 不過，如果以 '： ' 做為導引字元來支援具名引數，而且它不是參數名稱的一部分，則這會是： ":([z0-9_ $ #]\*）"。<br /><br /> 當然，如果資料來源不支援具名參數，則此項僅為 "?"。|  
|ParameterNameMaxLength|ssNoversion|參數名稱的最大長度 (以字元為單位)。 Visual Studio 要求如果支援參數名稱，則最大長度的最小值為 30 個字元。<br /><br /> 如果資料來源不支援具名參數，此屬性將傳回零。|  
|ParameterNamePattern|字串|符合有效參數名稱的規則運算式。 不同資料來源對可用於參數名稱的字元具有不同規則。<br /><br /> Visual Studio 要求如果支援參數名稱，則字元 "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" 為針對參數名稱有效的支援字元集最小值。|  
|QuotedIdentifierPattern|字串|符合引號識別項並具有識別項本身 (不帶有引號) 之相符值的規則運算式。 例如，如果資料來源使用雙引號識別引號識別碼，則這會是： "（\\（[^"]&#124; \\"\\"） *） "。|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|表示是否將引號識別項視為區分大小寫。|  
|StatementSeparatorPattern|字串|符合陳述式分隔符號的規則運算式。|  
|StringLiteralPattern|字串|符合字串常值並具有常值本身之相符值的規則運算式。 例如，如果資料來源使用單引號來識別字串，則這會是： "（' （[^ ']&#124;' '） * '）" '|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|指定資料來源支援何種型別的 SQL Join 陳述式。|  
  
## <a name="datatypes"></a>DataTypes  
 此結構描述集合會公開 .NET Framework Managed 提供者目前所連接之資料庫所支援資料型別的相關資訊。  
  
|ColumnName|DataType|說明|  
|----------------|--------------|-----------------|  
|TypeName|字串|提供者特定的資料型別名稱。|  
|ProviderDbType|ssNoversion|指定參數型別時，應使用之提供者特定的型別值。 例如，SqlDbType.Money 或 OracleType.Blob。|  
|ColumnSize|long|非數值資料行或參數的長度是指提供者為此型別定義的最大值或長度。<br /><br /> 若為字元資料，此為資料來源定義的最大或已定義的長度單位。 在 Oracle 中可以指定長度，然後指定某些字元資料型別的實際儲存大小。 如此僅會針對 Oracle 定義長度單位。<br /><br /> 若為日期-時間資料型別，則此為表示字串的長度 (假設最大值可以容納分數秒元件的精確度)。<br /><br /> 如果資料型別為數字，此為資料型別最大精確度的上限。|  
|CreateFormat|字串|表示如何將此資料行加入資料定義陳述式的格式字串，如 CREATE TABLE。 CreateParameter 陣列中的每個項目在格式字串都應使用「參數標記」來表示。<br /><br /> 例如，SQL 資料型別 DECIMAL 需要精確度及小數位數。 在此情況下，格式字串會是 "DECIMAL （{0}，{1}）"。|  
|CreateParameters|字串|建立此資料型別的資料行時，必須指定的建立參數。 每個建立參數會以逗號分隔，並按提供時的順序列在字串中。<br /><br /> 例如，SQL 資料型別 DECIMAL 需要精確度及小數位數。 在此情況下，建立參數應包含字串 "precision, scale"。<br /><br /> 在文字命令中，若要建立有效位數為10且小數位數為2的十進位資料行，則 CreateFormat 資料行的值可能{0}是{1}decimal （，） "，而完整的類型規格則為 decimal （10，2）。|  
|DataType|字串|資料型別之 .NET Framework 型別的名稱。|  
|IsAutoincrementable|bool|True 表示此資料型別的值可能會自動遞增。<br /><br /> False 表示此資料型別的值可能不會自動遞增。<br /><br /> 請注意，這僅表示此資料型別的資料行是否自動遞增，而不表示所有此型別的資料行都會自動遞增。|  
|IsBestMatch|bool|True 表示資料型別是資料儲存中所有資料型別，與 DataType 資料行之值所表示的 .NET Framework 資料型別間的最佳相符項。<br /><br /> False 表示資料型別不是最佳相符項。<br /><br /> 針對 DataType 資料行的值都相同的每個資料列集，IsBestMatch 資料行僅會在一個資料列中設定為 True。|  
|IsCaseSensitive|bool|True 表示資料型別為字元型別且區分大小寫。<br /><br /> False 表示資料型別不是字元型別或不區分大小寫。|  
|IsFixedLength|bool|True 表示資料定義語言 (DDL) 所建立之此資料型別的資料行為固定長度。<br /><br /> False 表示 DDL 所建立之此資料型別的資料行為可變長度。<br /><br /> DBNull.Value 表示仍不知道提供者會將此欄位對應至固定長度或是可變長度資料行。|  
|IsFixedPrecisionScale|bool|True 表示資料型別具有固定的精確度及小數位數。<br /><br /> False 表示資料型別不具有固定的精確度及小數位數。|  
|IsLong|bool|True 表示資料型別包含極長的資料，極長資料的定義與特定提供者有關。<br /><br /> False 表示資料型別不包含極長的資料。|  
|IsNullable|bool|True 表示資料型別可為 Null。<br /><br /> False 表示資料型別不可為 Null。<br /><br /> DBNull.Value 表示仍不知道資料型別是否可以為 Null。|  
|IsSearchable|bool|True 表示資料型別可用於使用任何運算子 (除 LIKE 述詞之外) 的 WHERE 子句。<br /><br /> False 表示資料型別無法用於使用任何運算子 (除 LIKE 述詞之外) 的 WHERE 子句。|  
|IsSearchableWithLike|bool|True 表示資料型別可與 LIKE 述詞搭配使用<br /><br /> False 表示資料型別無法與 LIKE 述詞搭配使用。|  
|IsUnsigned|bool|True 表示資料型別為 unsigned。<br /><br /> False 表示資料型別為 signed。<br /><br /> DBNull.Value 表示不適用於資料型別。|  
|MaximumScale|short|如果型別指示器為數字型別，則此為小數點右邊所允許的最大位數。 否則為 DBNull.Value。|  
|MinimumScale|short|如果型別指示器為數字型別，則此為小數點右邊所允許的最小位數。 否則為 DBNull.Value。|  
|IsConcurrencyType|bool|True 表示每次資料列變更及資料行的值與之前的值不同時，資料庫都會更新資料型別。<br /><br /> False 表示每次資料列變更時，資料庫不會更新資料型別。<br /><br /> DBNull.Value 表示資料庫不支援此型別的資料型別。|  
|IsLiteralSupported|bool|True 表示資料型別可表示為常值。<br /><br /> False 表示資料型別不可表示為常值。|  
|LiteralPrefix|字串|套用至指定常值的前置詞。|  
|LiteralSuffix|字串|套用至指定常值的後置詞。|  
|NativeDataType|String|NativeDataType 是用於公開資料型別之 OLE DB 型別的 OLE DB 特定資料行。|  
  
## <a name="restrictions"></a>限制  
 此結構描述集合公開目前用於連接資料庫的 .NET Framework Managed 提供者所支援之限制的相關資訊。  
  
|ColumnName|DataType|說明|  
|----------------|--------------|-----------------|  
|CollectionName|字串|會套用這些限制的集合名稱。|  
|RestrictionName|字串|集合中的限制名稱。|  
|RestrictionDefault|字串|忽略。|  
|RestrictionNumber|ssNoversion|此特定限制所屬之集合限制中的實際位置。|  
  
## <a name="reservedwords"></a>ReservedWords  
 此結構描述集合公開 .NET Framework Managed 提供者目前連接之資料庫所保留字的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|ReservedWord|字串|提供者特定的保留字。|  
  
## <a name="see-also"></a>另請參閱

- [擷取資料庫結構描述資訊](retrieving-database-schema-information.md)
- [GetSchema 和結構描述集合](getschema-and-schema-collections.md)
- [ADO.NET 概觀](ado-net-overview.md)
