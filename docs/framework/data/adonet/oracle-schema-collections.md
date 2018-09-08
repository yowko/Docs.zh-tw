---
title: Oracle 結構描述集合
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: 342c4cbe994eb983713be0f258e3a029df6739f8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217343"
---
# <a name="oracle-schema-collections"></a>Oracle 結構描述集合
除通用結構描述集合之外，Microsoft .NET Framework Data Provider for Oracle 還支援下列特定的結構描述集合：  
  
-   資料行  
  
-   Indexes  
  
-   IndexColumns  
  
-   程序  
  
-   序列  
  
-   Synonyms  
  
-   資料表  
  
-   使用者  
  
-   檢視  
  
-   函式  
  
-   封裝  
  
-   PackageBodies  
  
-   引數  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   ForeignKeys  
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## <a name="columns"></a>資料行  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|資料表、檢視表或叢集的擁有人。|  
|TABLE_NAME|String|資料表、檢視表或叢集名稱。|  
|COLUMN_NAME|String|資料行名稱。|  
|ID|Decimal|所建立之資料行的序號。|  
|資料型別|String|資料行的資料型別。|  
|LENGTH|Decimal|資料行的長度 (以位元組為單位)。|  
|PRECISION|Decimal|若為 NUMBER 資料型別，則是十進位精確度；若為 FLOAT 資料型別，則是二進位精確度；若為所有其他資料型別，則是 NULL。|  
|SCALE|Decimal|數字中小數點右邊的位數。|  
|NULLABLE|String|指定資料行是否允許 NULL。 若資料行沒有 NOT UNLL 條件約束，或者資料行是 PRIMARY KEY 的一部分，則此值為 N。|  
  
## <a name="indexes"></a>Indexes  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|索引的擁有人。|  
|INDEX_NAME|String|索引名稱。|  
|INDEX_TYPE|String|索引的型別 (NORMAL、BITMAP、FUNCTION-BASED NORMAL、FUNCTION-BASED BITMAP 或 DOMAIN)。|  
|TABLE_OWNER|String|索引物件的擁有人。|  
|TABLE_NAME|String|索引物件的名稱。|  
|TABLE_TYPE|String|索引物件的型別 (例如，TABLE、CLUSTER)。|  
|UNIQUENESS|String|索引是 UNIQUE 還是 NONUNIQUE。|  
|COMPRESSION|String|索引是 ENABLED 還是 DISABLED。|  
|PREFIX_LENGTH|Decimal|壓縮金鑰前置詞中的資料行數目。|  
|TABLESPACE_NAME|String|包含索引的表格區名稱。|  
|INI_TRANS|Decimal|交易的初始次數。|  
|MAX_TRANS|Decimal|交易的最大次數。|  
|INITIAL_EXTENT|Decimal|初始範圍的大小。|  
|NEXT_EXTENT|Decimal|次要範圍的大小。|  
|MIN_EXTENTS|Decimal|區段中允許的範圍最小數目。|  
|MAX_EXTENTS|Decimal|區段中允許的範圍最大數目。|  
|PCT_INCREASE|Decimal|範圍大小增加百分比。|  
|PCT_THRESHOLD|Decimal|每個索引項目所允許之區塊空間的臨界值百分比。|  
|INCLUDE_COLUMN|Decimal|要併入依索引進行組織之資料表主索引鍵 (非溢位) 索引的最後一個資料行的資料行 ID。 此資料行對應至 *_TAB_COLUMNS 資料字典檢視表的 COLUMN_ID 資料行。|  
|FREELISTS|Decimal|配置給此區段的處理序可用清單數目。|  
|FREELIST_GROUPS|Decimal|配置給此區段的可用清單群組數目。|  
|PCT_FREE|Decimal|區塊中可用空間的最小百分比。|  
|LOGGING|String|登入資訊。|  
|BLEVEL|Decimal|B*-Tree 層級：從其根區塊至分葉區塊的索引深度。 深度為 0 表示根區塊與分葉區塊相同。|  
|LEAF_BLOCKS|Decimal|索引中分葉區塊的數目。|  
|DISTINCT_KEYS|Decimal|不同索引值的數目。 對於強制 UNIQUE 條件約束及 PRIMARY KEY 條件約束的索引，此值與資料表中資料列的數目 (USER_TABLES.NUM_ROWS) 相同。|  
|AVG_LEAF_BLOCKS_PER_KEY|Decimal|分葉區塊的平均數目，在這些區塊中索引內每個不同的值都顯示為四捨五入成最接近的整數。 若為強制 UNIQUE 及 PRIMARY KEY 條件約束的索引，此值永遠為 1。|  
|AVG_DATA_BLOCKS_PER_KEY|Decimal|資料表中資料區塊的平均數目，索引中四捨五入成最接近之整數的不同值指向這些區塊。 此統計資料是包含資料列 (包含索引資料行的給定值) 之資料區塊的平均數目。|  
|CLUSTERING_FACTOR|Decimal|根據索引值，指出資料表中資料列順序數。|  
|狀態|String|非分割索引是 VALID 還是 UNUSABLE。|  
|NUM_ROWS|Decimal|索引中資料列的數目。|  
|SAMPLE_SIZE|Decimal|用於分析索引的範例大小。|  
|LAST_ANALYZED|DateTime|最近分析此索引的日期。|  
|DEGREE|String|掃描索引之每個執行個體的執行緒數目。|  
|INSTANCES|String|要在其上掃描索引的執行個體數目。|  
|PARTITIONED|String|此索引是否已分割 ([是]&#124;否)。|  
|TEMPORARY|String|索引是否在暫存資料表上。|  
|GENERATED|String|索引的名稱是否是系統產生 (Y&#124;N)。|  
|SECONDARY|String|索引是否為 Oracle9i Data Cartridge 之 ODCIIndexCreate 方法所建立的次要物件 (Y&#124;N)。|  
|BUFFER_POOL|String|要用於索引區塊之預設緩衝集區的名稱。|  
|USER_STATS|String|統計資料是否為使用者直接輸入的。|  
|DURATION|String|表示暫存資料表的持續期間：1) SYS$SESSION：在工作階段持續期間保留資料列，2) SYS$TRANSACTION：COMMIT 後刪除資料列，3) 若為永久資料表，則是 Null。|  
|PCT_DIRECT_ACCESS|Decimal|若為依索引進行組織之資料表上的次要索引，此為以 VALID 猜測的資料列百分比|  
|ITYP_OWNER|String|若為網域索引，此為索引型別的擁有人。|  
|ITYP_NAME|String|若為網域索引，此為索引型別的名稱。|  
|PARAMETERS|String|若為網域索引，此為參數字串。|  
|GLOBAL_STATS|String|若為分割的索引，表示統計資料是藉由整體分析索引收集的 (YES)，或者是藉由估計基礎索引分割區及子分割區而取得的 (NO)。|  
|DOMIDX_STATUS|String|反映網域索引的狀態。 NULL：指定的索引不是網域索引。 VALID：索引是有效的網域索引。 IDXTYP_INVLD：此網域索引的索引型別無效。|  
|DOMIDX_OPSTATUS|String|反映網域索引上執行的作業狀態：NULL：指定的索引不是網域索引。 VALID：作業執行完畢，未發生錯誤。 FAILED：作業失敗，發生錯誤。|  
|FUNCIDX_STATUS|String|表示功能型索引的狀態：NULL：這不是功能型索引，ENABLED：啟用功能型索引，DISABLED：停用功能型索引。|  
|JOIN_INDEX|String|表示這是否為聯結索引。|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|String|索引的擁有人。|  
|INDEX_NAME|String|索引名稱。|  
|TABLE_OWNER|String|資料表或叢集的擁有人。|  
|TABLE_NAME|String|資料表或叢集的名稱。|  
|COLUMN_NAME|String|物件型別資料行的資料行名稱或屬性。|  
|COLUMN_POSITION|Decimal|索引內資料行或屬性的位置。|  
|COLUMN_LENGTH|Decimal|資料行的索引長度。|  
|CHAR_LENGTH|Decimal|資料行的字碼指標長度上限。|  
|DESCEND|String|資料行是否依遞減順序排序。|  
  
## <a name="procedures"></a>程序  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人。|  
|OBJECT_NAME|String|物件名稱。|  
|SUBOBJECT_NAME|String|子物件的名稱 (例如，分割區)。|  
|OBJECT_ID|Decimal|物件的字典物件號碼。|  
|DATA_OBJECT_ID|Decimal|包含物件之區段的字典物件號碼。|  
|LAST_DDL_TIME|DateTime|DDL 命令對物件進行最後一次修改的時間戳記 (包括授權及撤銷)。|  
|TIMESTAMP|String|物件規格的時間戳記 (字元資料)。|  
|狀態|String|物件的狀態 (VALID、INVALID 或 N/A)。|  
|TEMPORARY|String|物件是否為暫存的 (目前的工作階段僅能看到置於此物件本身的資料)。|  
|GENERATED|String|是否已產生此物件系統的名稱？ (Y &AMP;#124; N)。|  
|SECONDARY|String|這是否為 Oracle9i Data Cartridge 之 ODCIIndexCreate 方法所建立的次要物件 (Y &#124; N)。|  
|CREATED|DateTime|建立物件的日期。|  
  
## <a name="sequences"></a>序列  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|String|序列的擁有人名稱。|  
|SEQUENCE_NAME|String|序列名稱。|  
|MIN_VALUE|Decimal|序列的最小值。|  
|MAX_VALUE|Decimal|序列的最大值。|  
|INCREMENT_BY|Decimal|序列遞增的值。|  
|CYCLE_FLAG|String|序列在達到限制時是否換行。|  
|ORDER_FLAG|String|是否按順序產生序號。|  
|CACHE_SIZE|Decimal|要快取的序號數目。|  
|LAST_NUMBER|Decimal|寫入磁碟的最後序號。 若序列使用快取，則寫入磁碟的號碼是置於序列快取的最後號碼。 此號碼可能大於所使用的最後序號。|  
  
## <a name="synonyms"></a>Synonyms  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|同義資料表的擁有人。|  
|SYNONYM_NAME|String|同義資料表名稱。|  
|TABLE_OWNER|String|同義資料表所參考的物件擁有人。|  
|TABLE_NAME|String|同義資料表所參考的物件名稱。|  
|DB_LINK|String|所參考的資料庫連結名稱 (如果有的話)。|  
  
## <a name="tables"></a>資料表  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|資料表的擁有人。|  
|TABLE_NAME|String|資料表名稱。|  
|TYPE|String|資料表型別。|  
  
## <a name="users"></a>使用者  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|NAME|String|使用者名稱。|  
|ID|Decimal|使用者的識別碼。|  
|CREATEDATE|DateTime|使用者建立日期。|  
  
## <a name="views"></a>檢視  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|檢視表的擁有人。|  
|VIEW_NAME|String|檢視表名稱。|  
|TEXT_LENGTH|Decimal|檢視表文字的長度。|  
|TEXT|String|檢視表文字。|  
|TYPE_TEXT_LENGTH|Decimal|具型別檢視表之型別子句的長度。|  
|TYPE_TEXT|String|具型別檢視表的型別子句。|  
|OID_TEXT_LENGTH|Decimal|具型別檢視表之 WITH OID 子句的長度。|  
|OID_TEXT|String|具型別檢視表的 WITH OID 子句。|  
|VIEW_TYPE_OWNER|String|檢視表型別的擁有人 (如果檢視表是具型別檢視表)。|  
|VIEW_TYPE|String|檢視表的型別 (如果檢視表是具型別檢視表)。|  
|SUPERVIEW_NAME|String|超級檢視表的名稱。|  
  
## <a name="functions"></a>函式  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人。|  
|OBJECT_NAME|String|物件名稱。|  
|SUBOBJECT_NAME|String|子物件的名稱 (例如，分割區)。|  
|OBJECT_ID|Decimal|物件的字典物件號碼。|  
|DATA_OBJECT_ID|Decimal|包含物件之區段的字典物件號碼。|  
|OBJECT_TYPE|String|物件的型別。|  
|CREATED|DateTime|建立物件的日期。|  
|LAST_DDL_TIME|DateTime|DDL 命令對物件進行最後一次修改的時間戳記 (包括授權及撤銷)。|  
|TIMESTAMP|String|物件規格的時間戳記 (字元資料)|  
|狀態|String|物件的狀態 (VALID、INVALID 或 N/A)。|  
|TEMPORARY|String|物件是否為暫存的 (目前的工作階段僅能看到置於此物件本身的資料)。|  
|GENERATED|String|是否已產生此物件系統的名稱？ (Y &AMP;#124; N)。|  
|SECONDARY|String|這是否為 Oracle9i Data Cartridge 之 ODCIIndexCreate 方法所建立的次要物件 (Y &#124; N)。|  
  
## <a name="packages"></a>封裝  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人。|  
|OBJECT_NAME|String|物件名稱。|  
|SUBOBJECT_NAME|String|子物件的名稱 (例如，分割區)。|  
|OBJECT_ID|Decimal|物件的字典物件號碼。|  
|DATA_OBJECT_ID|Decimal|包含物件之區段的字典物件號碼。|  
|LAST_DDL_TIME|DateTime|DDL 命令對物件進行最後一次修改的時間戳記 (包括授權及撤銷)。|  
|TIMESTAMP|String|物件規格的時間戳記 (字元資料)。|  
|狀態|String|物件的狀態 (VALID、INVALID 或 N/A)。|  
|TEMPORARY|String|物件是否為暫存的 (目前的工作階段僅能看到置於此物件本身的資料)。|  
|GENERATED|String|是否已產生此物件系統的名稱？ (Y &AMP;#124; N)。|  
|SECONDARY|String|這是否為 Oracle9i Data Cartridge 之 ODCIIndexCreate 方法所建立的次要物件 (Y &#124; N)。|  
|CREATED|DateTime|建立物件的日期。|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人。|  
|OBJECT_NAME|String|物件名稱。|  
|SUBOBJECT_NAME|String|子物件的名稱 (例如，分割區)。|  
|OBJECT_ID|Decimal|物件的字典物件號碼。|  
|DATA_OBJECT_ID|Decimal|包含物件之區段的字典物件號碼。|  
|LAST_DDL_TIME|DateTime|DDL 命令對物件進行最後一次修改的時間戳記 (包括授權及撤銷)。|  
|TIMESTAMP|String|物件規格的時間戳記 (字元資料)。|  
|狀態|String|物件的狀態 (VALID、INVALID 或 N/A)。|  
|TEMPORARY|String|物件是否為暫存的 (目前的工作階段僅能看到置於此物件本身的資料)。|  
|GENERATED|String|是否已產生此物件系統的名稱？ (Y &AMP;#124; N)。|  
|SECONDARY|String|這是否為 Oracle9i Data Cartridge 之 ODCIIndexCreate 方法所建立的次要物件 (Y &#124; N)。|  
|CREATED|DateTime|建立物件的日期。|  
  
## <a name="arguments"></a>引數  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人名稱。|  
|PACKAGE_NAME|String|封裝名稱。|  
|OBJECT_NAME|String|程序或函式的名稱。|  
|ARGUMENT_NAME|String|引數的名稱。|  
|POSITION|Decimal|在引數清單中的位置，若為函式傳回值，則為 NULL。|  
|SEQUENCE|Decimal|引數序列，包括所有的巢狀層次。|  
|DEFAULT_VALUE|String|引數的預設值。|  
|DEFAULT_LENGTH|Decimal|引數預設值的長度。|  
|IN_OUT|String|引數方向 (IN、OUT 或 IN/OUT)。|  
|DATA_LENGTH|Decimal|資料行的長度 (以位元組為單位)。|  
|DATA_PRECISION|Decimal|十進位數字 (NUMBER) 或二進位數字 (FLOAT) 的長度。|  
|DATA_SCALE|Decimal|數字中小數點右邊的位數。|  
|DATA_TYPE|String|引數的資料型別。|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|條件約束定義的擁有人。|  
|CONSTRAINT_NAME|String|條件約束定義的名稱。|  
|TABLE_NAME|String|與具有條件約束定義之資料表 (或檢視表) 相關的名稱。|  
|SEARCH_CONDITION|String|檢查條件約束之搜尋條件的文字。|  
|R_OWNER|String|參考條件約束中的參考資料表擁有人。|  
|R_CONSTRAINT_NAME|String|參考資料表之唯一的條件約束定義的名稱。|  
|DELETE_RULE|String|參考條件約束的刪除規則 (CASCADE 或 NO ACTION)。|  
|狀態|String|條件約束的強制狀態 (ENABLED 或 DISABLED)。|  
|DEFERRABLE|String|條件約束是否可以延遲。|  
|VALIDATED|String|是否所有資料均遵循條件約束 (VALIDATED 或 NOT VALIDATED)。|  
|GENERATED|String|條件約束的名稱是使用者產生的還是系統產生的。|  
|BAD|String|YES 值表示此條件約束以模稜兩可的方式指定世紀。 為避免因模稜兩可而導致錯誤，請使用四位數年份的 TO_DATE 函式重寫條件約束。|  
|RELY|String|是否已強制執行啟用的條件約束。|  
|LAST_CHANGE|DateTime|上次啟用或停用條件約束的時間|  
|INDEX_OWNER|String|擁有索引的使用者名稱|  
|INDEX_NAME|String|索引名稱|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|條件約束定義的擁有人。|  
|CONSTRAINT_NAME|String|條件約束定義的名稱。|  
|TABLE_NAME|String|與具有條件約束定義之資料表 (或檢視表) 相關的名稱。|  
|SEARCH_CONDITION|String|檢查條件約束之搜尋條件的文字。|  
|R_OWNER|String|參考條件約束中的參考資料表擁有人。|  
|R_CONSTRAINT_NAME|String|參考資料表之唯一的條件約束定義的名稱。|  
|DELETE_RULE|String|參考條件約束的刪除規則 (CASCADE 或 NO ACTION)。|  
|狀態|String|條件約束的強制狀態 (ENABLED 或 DISABLED)。|  
|DEFERRABLE|String|條件約束是否可以延遲。|  
|VALIDATED|String|是否所有資料均遵循條件約束 (VALIDATED 或 NOT VALIDATED)。|  
|GENERATED|String|條件約束的名稱是使用者產生的還是系統產生的。|  
|BAD|String|YES 值表示此條件約束以模稜兩可的方式指定世紀。 為避免因模稜兩可而導致錯誤，請使用四位數年份的 TO_DATE 函式重寫條件約束。|  
|RELY|String|是否已強制執行啟用的條件約束。|  
|LAST_CHANGE|DateTime|上次啟用或停用條件約束的時間。|  
|INDEX_OWNER|String|擁有索引的使用者名稱。|  
|INDEX_NAME|String|索引名稱。|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|String|條件約束定義的名稱。|  
|PRIMARY_KEY_OWNER|String|條件約束定義的擁有人。|  
|PRIMARY_KEY_TABLE_NAME|String|與具有條件約束定義之資料表 (或檢視表) 相關的名稱|  
|FOREIGN_KEY_OWNER|String|條件約束定義的擁有人。|  
|FOREIGN_KEY_CONSTRIANT_NAME|String|條件約束定義的名稱。|  
|FOREIGN_KEY_TABLE_NAME|String|與具有條件約束定義之資料表 (或檢視表) 相關的名稱。|  
|SEARCH_CONDITION|String|檢查條件約束之搜尋條件的文字|  
|R_OWNER|String|參考條件約束中的參考資料表擁有人。|  
|R_CONSTRAINT_NAME|String|參考資料表之唯一的條件約束定義的名稱。|  
|DELETE_RULE|String|參考條件約束的刪除規則 (CASCADE 或 NO ACTION)。|  
|狀態|String|條件約束的強制狀態 (ENABLED 或 DISABLED)。|  
|VALIDATED|String|是否所有資料均遵循條件約束 (VALIDATED 或 NOT VALIDATED)。|  
|GENERATED|String|條件約束的名稱是使用者產生的還是系統產生的。|  
|RELY|String|是否已強制執行啟用的條件約束。|  
|LAST_CHANGE|DateTime|上次啟用或停用條件約束的時間。|  
|INDEX_OWNER|String|擁有索引的使用者名稱。|  
|INDEX_NAME|String|索引名稱。|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|條件約束定義的擁有人。|  
|CONSTRAINT_NAME|String|條件約束定義的名稱。|  
|TABLE_NAME|String|具有條件約束定義的資料表名稱。|  
|COLUMN_NAME|String|條件約束定義中指定之物件型別資料行的資料行或屬性名稱。|  
|POSITION|Decimal|物件定義中資料行或屬性的原始位置。|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|OWNER|String|物件的擁有人。|  
|OBJECT_NAME|String|程序或函式的名稱。|  
|PACKAGE_NAME|String|程序或函式的名稱。|  
|OBJECT_ID|Decimal|物件的物件號碼。|  
|OVERLOAD|String|多載唯一識別項。|  
|ARGUMENT_NAME|String|引數的名稱。|  
|POSITION|Decimal|在引數清單中的位置，若為函式傳回值，則為 NULL。|  
|SEQUENCE|Decimal|引數序列，包括所有的巢狀層次。|  
|DATA_LEVEL|Decimal|綜合型別之引數的巢狀深度。|  
|DATA_TYPE|String|引數的資料型別。|  
|DEFAULT_VALUE|String|引數的預設值。|  
|DEFAULT_LENGTH|Decimal|引數預設值的長度。|  
|IN_OUT|String|引數方向 (IN、OUT 或 IN/OUT)。|  
|DATA_LENGTH|Decimal|資料行的長度 (以位元組為單位)。|  
|DATA_PRECISION|Decimal|十進位數字 (NUMBER) 或二進位數字 (FLOAT) 的長度。|  
|DATA_SCALE|Decimal|數字中小數點右邊的位數。|  
|RADIX|Decimal|數字的引數基數。|  
|CHARACTER_SET_NAME|String|引數的字元集名稱。|  
|TYPE_OWNER|String|引數型別的擁有人。|  
|TYPE_NAME|String|引數型別的名稱。 若型別是封裝本機型別 (即在封裝規格中宣告)，則此資料行會顯示封裝的名稱。|  
|TYPE_SUBNAME|String|僅與封裝本機型別相關。 顯示 TYPE_NAME 資料行中識別之封裝中宣告的型別名稱。|  
|TYPE_LINK|String|TYPE_NAME 資料行中識別的封裝是遠端封裝時，僅與封裝本機型別相關。 此資料行顯示用於參考遠端封裝的資料庫連結。|  
|PLS_TYPE|String|若為數字引數，此為引數的 PL/SQL 型別名稱。 否則，為 Null。|  
|CHAR_LENGTH|Decimal|字串資料型別的字元限制。|  
|CHAR_USED|String|指出位元組限制 (B) 或字元限制 (C) 是否為字串的正式限制。|  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
