---
title: 一般結構描述集合
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 157330304ac656ddbdbb18408ca5144566746808
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870259"
---
# <a name="common-schema-collections"></a>一般結構描述集合
通用結構描述集合是由每個 .NET Framework Managed 提供者所實作的結構描述集合。 您可以查詢來判斷支援的結構描述集合清單，藉由呼叫.NET Framework managed 提供者**GetSchema**方法沒有引數，或以結構描述集合名稱"MetaDataCollections"。 這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。 這些集合會描述所有必要資料行。 如果願意，提供者可以隨意加入其他資料行。 例如，`SqlClient` 及 `OracleClient` 會將 ParameterName 加入限制集合。  
  
 如果提供者無法決定必要資料行的值，則會傳回 Null。  
  
 如需使用詳細資訊**GetSchema**方法，請參閱[GetSchema 和結構描述集合](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)。  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 此結構描述集合會公開目前用於連接至資料庫之 .NET Framework Managed 提供者所支援的所有結構描述集合的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|CollectionName|字串|要傳遞給集合的名稱**GetSchema**傳回集合的方法。|  
|NumberOfRestrictions|int|可以為集合指定的限制數目。|  
|NumberOfIdentifierParts|int|複合識別項/資料庫物件名稱的部分數目。 例如，在 SQL Server 中，資料表數目應為 3，資料行數目應為 4。 在 Oracle 中，資料表數目應為 2，資料行數目應為 3。|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 此結構描述集合會公開 .NET Framework Managed 提供者目前所連接之資料來源的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|符合複合識別項中複合分隔符號的規則運算式。 例如，"\\。 」 （適用於 SQL Server) 或 「\@&#124;\\。 」 (適用於 Oracle)。<br /><br /> 複合識別項通常是什麼使用於資料庫物件名稱，例如： pubs.dbo.authors 或 pubs\@dbo.authors。<br /><br /> 針對 SQL Server，請使用規則運算式 「\\。 」。 針對 OracleClient 則使用 「\@&#124;\\。 」。<br /><br /> 若為 ODBC，請使用 Catalog_name_seperator。<br /><br /> 若為 OLE DB，請使用 DBLITERAL_CATALOG_SEPARATOR 或 DBLITERAL_SCHEMA_SEPARATOR。|  
|DataSourceProductName|string|提供者存取的產品名稱，如 "Oracle" 或 "SQLServer"。|  
|DataSourceProductVersion|string|表示提供者存取的產品版本，使用資料來源原生格式，而非 Microsoft 格式。<br /><br /> 在某些情況下，DataSourceProductVersion 及 DataSourceProductVersionNormalized 將為同一值。 若為 OLE DB 及 ODBC，這些值將永遠相同，因為它們對應於基礎原生 API 中的同一函式呼叫。|  
|DataSourceProductVersionNormalized|string|資料來源的正規化版本，可使用 `String.Compare()` 進行比較。 它的格式對提供者的所有版本來說都一致，這可以防止版本 10 在版本 1 與版本 2 之間排序。<br /><br /> 例如，Oracle 提供者會針對其正規化版本，會使 Oracle 8i 資料來源傳回"08.01.07.04.01"中，使用"nn.nn.nn.nn.nn 」 格式。 SQL Server 會使用一般的 Microsoft"nn.nn.nnnn"格式。<br /><br /> 在某些情況下，DataSourceProductVersion 及 DataSourceProductVersionNormalized 將為同一值。 若為 OLE DB 及 ODBC，這些值將永遠相同，因為它們對應於基礎原生 API 中的同一函式呼叫。|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|指定 GROUP BY 子句中的資料行與選取清單中的非彙總資料行的關係。|  
|IdentifierPattern|string|符合識別項並具有識別項相符值的規則運算式。 例如 "[A-Za-z0-9_#$]"。|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|表示是否將非引號識別項視為區分大小寫。|  
|OrderByColumnsInSelect|bool|指定 ORDER BY 子句中的資料行是否必須包含於選取清單中。 True 值表示其必須包含於選取清單中，False 值表示其不必包含於選取清單中。|  
|ParameterMarkerFormat|string|表示如何格式化參數的格式字串。<br /><br /> 如果資料來源支援具名參數，則此字串中的第一個替代符號位置應為要格式化參數名稱的位置。<br /><br /> 例如，如果資料來源要求對參數進行命名，並加上 ':' 這會是":{0}"。 使用參數名稱 "p1" 對進行格式化時，產生的字串為 ":p1"。<br /><br /> 如果資料來源要求參數前面會加上 '\@'，但名稱中已包含它們，這會是'{0}'，並格式化一個名為參數的結果 」\@p1 」 將只是 「\@p1"。<br /><br /> 資料來源不要求具名的參數而要求使用 '？ ' 字元，只要指定的格式字串 '？ '，這會忽略參數名稱。 針對 OLE DB 將傳回 '?'。|  
|ParameterMarkerPattern|string|符合參數標記的規則運算式。 它會具有參數名稱的相符值 (如果有的話)。<br /><br /> 例如，如果支援具名的參數 '\@' 導引字元包括在參數名稱，這會是:"(\@[A-A-za-a-za-z0-9_$ #] *)"。<br /><br /> 不過，如果支援具名的參數 ':' 做為導引字元，且它不屬於參數名稱，這會是:": ([A-A-za-a-za-z0-9_$ #]\*) 」。<br /><br /> 當然，如果資料來源不支援具名參數，則此項僅為 "?"。|  
|ParameterNameMaxLength|int|參數名稱的最大長度 (以字元為單位)。 Visual Studio 要求如果支援參數名稱，則最大長度的最小值為 30 個字元。<br /><br /> 如果資料來源不支援具名參數，此屬性將傳回零。|  
|ParameterNamePattern|string|符合有效參數名稱的規則運算式。 不同資料來源對可用於參數名稱的字元具有不同規則。<br /><br /> Visual Studio 要求如果支援參數名稱，則字元 "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" 為針對參數名稱有效的支援字元集最小值。|  
|QuotedIdentifierPattern|string|符合引號識別項並具有識別項本身 (不帶有引號) 之相符值的規則運算式。 例如，如果資料來源使用雙引號識別引號識別項，這會是: 「 (([^\\"]&#124;\\"\\") *)"。|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|表示是否將引號識別項視為區分大小寫。|  
|StatementSeparatorPattern|string|符合陳述式分隔符號的規則運算式。|  
|StringLiteralPattern|string|符合字串常值並具有常值本身之相符值的規則運算式。 例如，如果資料來源使用單引號識別字串，此項為:"('([^']&#124;'') *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|指定資料來源支援何種型別的 SQL Join 陳述式。|  
  
## <a name="datatypes"></a>DataTypes  
 此結構描述集合會公開 .NET Framework Managed 提供者目前所連接之資料庫所支援資料型別的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TypeName|string|提供者特定的資料型別名稱。|  
|ProviderDbType|int|指定參數型別時，應使用之提供者特定的型別值。 例如，SqlDbType.Money 或 OracleType.Blob。|  
|ColumnSize|long|非數值資料行或參數的長度是指提供者為此型別定義的最大值或長度。<br /><br /> 若為字元資料，此為資料來源定義的最大或已定義的長度單位。 在 Oracle 中可以指定長度，然後指定某些字元資料型別的實際儲存大小。 如此僅會針對 Oracle 定義長度單位。<br /><br /> 若為日期-時間資料型別，則此為表示字串的長度 (假設最大值可以容納分數秒元件的精確度)。<br /><br /> 如果資料型別為數字，此為資料型別最大精確度的上限。|  
|CreateFormat|string|表示如何將此資料行加入資料定義陳述式的格式字串，如 CREATE TABLE。 CreateParameter 陣列中的每個項目在格式字串都應使用「參數標記」來表示。<br /><br /> 例如，SQL 資料型別 DECIMAL 需要精確度及小數位數。 在此情況下，格式字串會以 「 十進位 ({0}，{1}) 」。|  
|CreateParameters|string|建立此資料型別的資料行時，必須指定的建立參數。 每個建立參數會以逗號分隔，並按提供時的順序列在字串中。<br /><br /> 例如，SQL 資料型別 DECIMAL 需要精確度及小數位數。 在此情況下，建立參數應包含字串 "precision, scale"。<br /><br /> 在文字命令使用精確度為 10，小數位數 2 建立 DECIMAL 資料行中，CreateFormat 資料行的值可能為 DECIMAL ({0}，{1}) 」 的完整的型別規格則為 DECIMAL(10,2)。|  
|DataType|string|資料型別之 .NET Framework 型別的名稱。|  
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
|LiteralPrefix|string|套用至指定常值的前置詞。|  
|Datatypes|字串|套用至指定常值的後置詞。|  
|NativeDataType|String|NativeDataType 是用於公開資料型別之 OLE DB 型別的 OLE DB 特定資料行。|  
  
## <a name="restrictions"></a>限制  
 此結構描述集合公開目前用於連接資料庫的 .NET Framework Managed 提供者所支援之限制的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|CollectionName|string|會套用這些限制的集合名稱。|  
|RestrictionName|string|集合中的限制名稱。|  
|RestrictionDefault|string|忽略。|  
|RestrictionNumber|int|此特定限制所屬之集合限制中的實際位置。|  
  
## <a name="reservedwords"></a>ReservedWords  
 此結構描述集合公開 .NET Framework Managed 提供者目前連接之資料庫所保留字的相關資訊。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|Reservedwords|字串|提供者特定的保留的字。|  
  
## <a name="see-also"></a>另請參閱  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema 和結構描述集合](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
