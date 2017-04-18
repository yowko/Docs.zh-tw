---
title: "SQL-CLR 型別對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# SQL-CLR 型別對應
在 LINQ to SQL 中，關聯式資料庫的資料模型會對應至以您選擇之程式語言表示的物件模型 \(Object Model\)。  執行應用程式時，LINQ to SQL 會將物件模型中的 Language Integrated Query \(LINQ\) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。  當資料庫傳回結果時，LINQ to SQL 會將結果轉譯回您可以在自己的程式語言中處理的物件。  
  
 若要在物件模型與資料庫之間轉譯資料，您必須定義「*型別對應*」\(Type Mapping\)。  LINQ to SQL 會使用型別對應來比對每個 Common Language Runtime \(CLR\) 型別與特定 SQL Server 型別。  您可以使用以屬性 \(Attribute\) 為基礎的對應，在物件模型內部定義型別對應和其他對應資訊，例如資料庫結構與資料表關聯性 \(Relationship\)。  此外，您也可以使用外部對應檔案，在物件模型外部指定對應資訊。  如需詳細資訊，請參閱[以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) 和[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
 這個主題將討論下列重點：  
  
-   [預設型別對應](#DefaultTypeMapping)  
  
-   [型別對應的執行階段行為對照表](#BehaviorMatrix)  
  
-   [CLR 與 SQL 執行之間的行為差異](#BehaviorDiffs)  
  
-   [Enum 對應](#EnumMapping)  
  
-   [數字對應](#NumericMapping)  
  
-   [文字和 XML 對應](#TextMapping)  
  
-   [日期和時間對應](#DateMapping)  
  
-   [二進位對應](#BinaryMapping)  
  
-   [其他對應](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## 預設型別對應  
 您可以使用物件關聯式設計工具 \(O\/R 設計工具\) 或 SQLMetal 命令列工具，自動建立物件模型或外部對應檔案。  這些工具的預設型別對應會定義選擇哪些 CLR 型別來對應至 SQL Server 資料庫內部的資料行。  如需使用這些工具的詳細資訊，請參閱[建立物件模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)。  
  
 您也可以根據物件模型或外部對應檔案中的對應資訊，使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 方法來建立 SQL Server 資料庫。  <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 方法的預設型別對應會定義建立哪些 SQL Server 資料行型別來對應至物件模型中的 CLR 型別。  如需詳細資訊，請參閱[HOW TO：動態建立資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)。  
  
<a name="BehaviorMatrix"></a>   
## 型別對應的執行階段行為對照表  
 下圖顯示從資料庫中擷取資料或將資料儲存至資料庫時，特定型別對應的預期執行階段行為。  除了序列化 \(Serialization\) 以外，LINQ to SQL 不支援此對照表中未指定之任何 CLR 或 SQL Server 資料型別之間的對應。  如需序列化支援的詳細資訊，請參閱[二進位序列化](#BinarySerialization)。  
  
> [!NOTE]
>  在資料庫之間來回轉譯時，某些型別對應可能會造成溢位或資料遺失的例外狀況 \(Exception\)。  
  
### 自訂型別對應  
 在 LINQ to SQL 中，您不會受限於 O\/R 設計工具、SQLMetal 和 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 方法的預設型別對應。  您可以在 DBML 檔案中明確指定自訂型別對應，藉以建立這些對應。  然後，您就可以使用該 DBML 檔案來建立物件模型程式碼和對應檔案。  如需詳細資訊，請參閱 [SQL\-CLR 自訂型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md)。  
  
<a name="BehaviorDiffs"></a>   
## CLR 與 SQL 執行之間的行為差異  
 由於 CLR 與 SQL Server 之間存在精確度和執行差異，所以您可能會收到不同的結果或產生不同的行為，端視執行計算的位置而定。  在 LINQ to SQL 查詢中執行的計算實際上會轉譯成 Transact\-SQL，然後在 SQL Server 資料庫上執行。  在 LINQ to SQL 查詢外部執行的計算則會在 CLR 的內容中執行。  
  
 例如，下面是 CLR 與 SQL Server 之間的一些行為差異：  
  
-   SQL Server 排序某些資料型別的方式與 CLR 中對等資料型別的排序方式不同。  例如，SQL Server 資料型別 `UNIQUEIDENTIFIER` 的排序方式就與 CLR 資料型別 <xref:System.Guid?displayProperty=fullName> 的排序方式不同。  
  
-   SQL Server 處理某些字串比較作業的方式與 CLR 不同。  在 SQL Server 中，字串比較行為會因伺服器的定序 \(Collation\) 設定而不同。  如需詳細資訊，請參閱[使用定序](http://go.microsoft.com/fwlink/?LinkId=115330)。  
  
-   SQL Server 與 CLR 可能會針對某些對應函式傳回不同的值。  例如，等號比較函式便有所不同，因為如果兩個字串只有尾端泛空白字元 \(White Space\) 不同，SQL Server 就會將它們視為相等，而 CLR 則會將它們視為不相等。  
  
<a name="EnumMapping"></a>   
## Enum 對應  
 LINQ to SQL 支援以下列兩種方式將 CLR <xref:System.Enum?displayProperty=fullName> 型別對應至 SQL Server 型別：  
  
-   對應至 SQL 數字型別 \(`TINYINT`、`SMALLINT`、`INT`、`BIGINT`\)  
  
     當您將 CLR <xref:System.Enum?displayProperty=fullName> 型別對應至 SQL 數字型別 \(Numeric Type\) 時，就會將 CLR <xref:System.Enum?displayProperty=fullName> 的基礎整數值對應至 SQL Server 資料庫資料行的值。  例如，如果名為 <xref:System.Enum?displayProperty=fullName> 的 `DaysOfWeek` 包含名為 `Tue` 而且具有基礎整數值 3 的成員，則該成員就會對應至資料庫值 3。  
  
-   對應至 SQL 文字型別 \(`CHAR`、`NCHAR`、`VARCHAR`、`NVARCHAR`\)  
  
     當您將 CLR <xref:System.Enum?displayProperty=fullName> 型別對應至 SQL 文字型別時，SQL 資料庫值會對應至 CLR <xref:System.Enum?displayProperty=fullName> 成員的名稱。  例如，如果名為 <xref:System.Enum?displayProperty=fullName> 的 `DaysOfWeek` 包含名為 `Tue` 而且具有基礎整數值 3 的成員，則該成員就會對應至資料庫值 `Tue`。  
  
> [!NOTE]
>  將 SQL 文字型別對應至 CLR <xref:System.Enum?displayProperty=fullName> 時，請單獨在對應的 SQL 資料行中加入 <xref:System.Enum> 成員的名稱。  <xref:System.Enum> 對應的 SQL 資料行不支援其他值。  
  
 O\/R 設計工具和 SQLMetal 命令列工具無法自動將 SQL 型別對應至 CLR <xref:System.Enum> 類別 \(Class\)。  您必須針對供 O\/R 設計工具和 SQLMetal 使用自訂 DBML 檔案，藉以明確設定此對應。  如需自訂類型對應的詳細資訊，請參閱 [SQL\-CLR 自訂型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md)。  
  
 由於適用於列舉型別 \(Enumeration\) 的 SQL 資料行與其他數值和文字資料行具有相同的型別，所以這些工具將無法辨識您的意圖，而且它們會預設為對應，如下列「[數字對應](#NumericMapping)」和「[文字和 XML 對應](#TextMapping)」章節所述。  如需使用 DBML 檔案來產生程式碼的詳細資訊，請參閱 [LINQ to SQL 的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法會建立數字型別的 SQL 資料行來對應 CLR <xref:System.Enum?displayProperty=fullName> 型別。  
  
<a name="NumericMapping"></a>   
## 數字對應  
 LINQ to SQL 可讓您對應許多 CLR 和 SQL Server 數字型別。  下表顯示根據資料庫建置物件模型或外部對應檔案時，O\/R 設計工具和 SQLMetal 所選取的 CLR 型別。  
  
|SQL Server 型別|O\/R 設計工具和 SQLMetal 所使用的預設 CLR 型別對應|  
|-------------------|-----------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=fullName>|  
|`TINYINT`|<xref:System.Int16?displayProperty=fullName>|  
|`INT`|<xref:System.Int32?displayProperty=fullName>|  
|`BIGINT`|<xref:System.Int64?displayProperty=fullName>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=fullName>|  
|`MONEY`|<xref:System.Decimal?displayProperty=fullName>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=fullName>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=fullName>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=fullName>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=fullName>|  
  
 下表顯示 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法用於定義建立哪些 SQL 資料行型別來對應至 CLR 型別 \(定義於物件模型或外部對應檔案中\) 的預設型別對應。  
  
|CLR 型別|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 所使用的預設 SQL Server 型別|  
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=fullName>|`BIT`|  
|<xref:System.Byte?displayProperty=fullName>|`TINYINT`|  
|<xref:System.Int16?displayProperty=fullName>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=fullName>|`INT`|  
|<xref:System.Int64?displayProperty=fullName>|`BIGINT`|  
|<xref:System.SByte?displayProperty=fullName>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=fullName>|`INT`|  
|<xref:System.UInt32?displayProperty=fullName>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=fullName>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=fullName>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=fullName>|`REAL`|  
|<xref:System.Double?displayProperty=fullName>|`FLOAT`|  
  
 雖然還有許多其他數字對應可供您選擇，但是在資料庫之間來回轉譯時，某些對應可能會造成溢位或資料遺失的例外狀況。  如需詳細資訊，請參閱[型別對應的執行階段行為對照表](#BehaviorMatrix)。  
  
### Decimal 和 Money 型別  
 SQL Server `DECIMAL` 型別的預設精確度 \(小數點左右的 18 個十進位數字\) 小於預設搭配使用之 CLR <xref:System.Decima?displayProperty=fullName>l 型別的精確度。  當您將資料儲存至資料庫時，這可能會導致精確度遺失。  不過，如果 SQL Server `DECIMAL` 型別設定為大於 29 個位數的精確度，可能會發生完全相反的情況。  當 SQL Server `DECIMAL` 型別已經設定為大於 CLR <xref:System.Decimal?displayProperty=fullName> 的精確度時，如果從資料庫中擷取資料，就可能會發生精確度遺失。  
  
 SQL Server `MONEY` 和 `SMALLMONEY` 型別 \(預設也會與 CLR <xref:System.Decimal?displayProperty=fullName> 型別搭配使用\) 具有更小的精確度，而且將資料儲存至資料庫時，可能會造成溢位或資料遺失的例外狀況。  
  
<a name="TextMapping"></a>   
## 文字和 XML 對應  
 還有許多以文字為基礎的型別和 XML 型別，可讓您透過 LINQ to SQL 進行對應。  下表顯示根據資料庫建置物件模型或外部對應檔案時，O\/R 設計工具和 SQLMetal 所選取的 CLR 型別。  
  
|SQL Server 型別|O\/R 設計工具和 SQLMetal 所使用的預設 CLR 型別對應|  
|-------------------|-----------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=fullName>|  
|`NCHAR`|<xref:System.String?displayProperty=fullName>|  
|`VARCHAR`|<xref:System.String?displayProperty=fullName>|  
|`NVARCHAR`|<xref:System.String?displayProperty=fullName>|  
|`TEXT`|<xref:System.String?displayProperty=fullName>|  
|`NTEXT`|<xref:System.String?displayProperty=fullName>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=fullName>|  
  
 下表顯示 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法用於定義建立哪些 SQL 資料行型別來對應至 CLR 型別 \(定義於物件模型或外部對應檔案中\) 的預設型別對應。  
  
|CLR 型別|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 所使用的預設 SQL Server 型別|  
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=fullName>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=fullName>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=fullName>\[\]|`NVARCHAR(4000)`|  
|實作 `Parse()` 和 `ToString()` 的自訂型別|`NVARCHAR(MAX)`|  
  
 雖然還有許多其他以文字為基礎的對應和 XML 對應可供您選擇，但是在資料庫之間來回轉譯時，某些對應可能會造成溢位或資料遺失的例外狀況。  如需詳細資訊，請參閱[型別對應的執行階段行為對照表](#BehaviorMatrix)。  
  
### XML 型別  
 從 Microsoft SQL Server 2005 開始，就提供了 SQL Server `XML` 資料型別。  您可以將 SQL Server `XML` 資料類型對應至 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument> 或 <xref:System.String>。  如果資料行儲存的 XML 片段無法讀入 <xref:System.Xml.Linq.XElement> 中，則該資料行必須對應至 <xref:System.String>，以免發生執行階段錯誤。  必須對應至 <xref:System.String> 的 XML 片段包括：  
  
-   XML 項目的序列  
  
-   屬性  
  
-   公用識別項 \(PI\)  
  
-   註解  
  
 雖然您可以將 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 對應至 SQL Server \(如[型別對應的執行階段行為對照表](#BehaviorMatrix)中所示\)，但是 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法沒有這些型別的預設 SQL Server 型別對應。  
  
### 自訂型別  
 如果某個類別 \(Class\) 實作 `Parse()` 和 `ToString()`，您就可以將此物件對應至任何 SQL 文字型別 \(`CHAR`、 `NCHAR`、`VARCHAR`、`NVARCHAR`、`TEXT`、`NTEXT` 或 `XML`\)。  此物件會透過將 `ToString()` 所傳回的值傳送至對應的資料庫資料行，儲存在資料庫中。  此物件的重建方式是針對資料庫所傳回的字串叫用 \(Invoke\) `Parse()`。  
  
> [!NOTE]
>  LINQ to SQL 不支援使用 <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=fullName> 進行序列化。  
  
<a name="DateMapping"></a>   
## 日期和時間對應  
 在 LINQ to SQL 中，您可以對應許多 SQL Server 日期和時間型別。  下表顯示根據資料庫建置物件模型或外部對應檔案時，O\/R 設計工具和 SQLMetal 所選取的 CLR 型別。  
  
|SQL Server 型別|O\/R 設計工具和 SQLMetal 所使用的預設 CLR 型別對應|  
|-------------------|-----------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=fullName>|  
|`DATE`|<xref:System.DateTime?displayProperty=fullName>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=fullName>|  
  
 下表顯示 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法用於定義建立哪些 SQL 資料行型別來對應至 CLR 型別 \(定義於物件模型或外部對應檔案中\) 的預設型別對應。  
  
|CLR 型別|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 所使用的預設 SQL Server 型別|  
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=fullName>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=fullName>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=fullName>|`TIME`|  
  
 雖然還有許多其他日期和時間對應可供您選擇，但是在資料庫之間來回轉譯時，某些對應可能會造成溢位或資料遺失的例外狀況。  如需詳細資訊，請參閱[型別對應的執行階段行為對照表](#BehaviorMatrix)。  
  
> [!NOTE]
>  從 Microsoft SQL Server 2008 開始，就提供了 SQL Server 型別 `DATETIME2`、`DATETIMEOFFSET`、`DATE` 和 `TIME`。  從 .NET Framework 3.5 版 SP1 開始，LINQ to SQL 支援對應至這些新的型別。  
  
### System.Datetime  
 CLR <xref:System.DateTime?displayProperty=fullName> 型別的範圍和精確度大於 SQL Server `DATETIME` 型別的範圍和精確度，而這是 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法的預設型別對應。  若要協助避免與超出 `DATETIME` 範圍之日期相關的例外狀況，請使用 `DATETIME2` \(從 Microsoft SQL Server 2008 開始提供\)。  `DATETIME2` 可以比對 CLR <xref:System.DateTime?displayProperty=fullName> 的範圍和精確度。  
  
 SQL Server 日期沒有 <xref:System.TimeZone> 的概念，而這是 CLR 中完全支援的功能。  不論原始 <xref:System.TimeZone> 資訊為何，<xref:System.TimeZone> 值會原樣儲存至資料庫，而不進行 <xref:System.DateTimeKind> 轉換。  從資料庫擷取 <xref:System.DateTime> 值時，這個值會原樣載入至 <xref:System.DateTime>，並將 <xref:System.DateTimeKind> 設為 <xref:System.DateTimeKind> 中。  如需支援之 <xref:System.DateTime?displayProperty=fullName> 方法的詳細資訊，請參閱 [System.DateTime 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md)。  
  
### System.TimeSpan  
 Microsoft SQL Server 2008 和 .NET Framework 3.5 SP1 可讓您將 CLR <xref:System.TimeSpan?displayProperty=fullName> 型別對應至 SQL Server `TIME` 型別。  不過，CLR <xref:System.TimeSpan?displayProperty=fullName> 所支援的範圍與 SQL Server `TIME` 型別所支援的範圍之間具有大幅差異。  將小於 0 或大於 23:59:59.9999999 小時的值對應至 SQL `TIME` 將會造成溢位的例外狀況。  如需詳細資訊，請參閱 [System.TimeSpan 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md)。  
  
 在 Microsoft SQL Server 2000 和 SQL Server 2005 中，您無法將資料庫欄位對應至 <xref:System.TimeSpan>。  但是，支援 <xref:System.TimeSpan> 的作業，因為 <xref:System.TimeSpan> 值可以從 <xref:System.DateTime> 減法傳回，或引進運算式中做為常值或繫結變數。  
  
<a name="BinaryMapping"></a>   
## 二進位對應  
 可對應至 CLR 型別 <xref:System.Data.Linq.Binary?displayProperty=fullName> 的 SQL Server 型別有許多種。  下表顯示根據資料庫建置物件模型或外部對應檔案時，導致 O\/R 設計工具和 SQLMetal 定義 CLR <xref:System.Data.Linq.Binary?displayProperty=fullName> 型別的 SQL Server 型別。  
  
|SQL Server 型別|O\/R 設計工具和 SQLMetal 所使用的預設 CLR 型別對應|  
|-------------------|-----------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|具有 `VARBINARY(MAX)` 屬性的 `FILESTREAM`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
  
 下表顯示 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法用於定義建立哪些 SQL 資料行型別來對應至 CLR 型別 \(定義於物件模型或外部對應檔案中\) 的預設型別對應。  
  
|CLR 型別|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 所使用的預設 SQL Server 型別|  
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=fullName>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=fullName>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>|`VARBINARY(MAX)`|  
  
 雖然還有許多其他二進位對應可供您選擇，但是在資料庫之間來回轉譯時，某些對應可能會造成溢位或資料遺失的例外狀況。  如需詳細資訊，請參閱[型別對應的執行階段行為對照表](#BehaviorMatrix)。  
  
### SQL Server FILESTREAM  
 從 Microsoft SQL Server 2008 開始，就提供了 `FILESTREAM` 資料行的 `VARBINARY(MAX)` 屬性。從 .NET Framework 3.5 版 SP1 開始，您就可以透過 LINQ to SQL 對應至此屬性。  
  
 雖然您可以將具有 `VARBINARY(MAX)` 屬性的 `FILESTREAM` 資料行對應至 <xref:System.Data.Linq.Binary> 物件，但是 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法無法自動建立具有 `FILESTREAM` 屬性的資料行。  如需有關 `FILESTREAM` 的詳細資訊，請參閱《Microsoft SQL Server 線上叢書》中的 [FILESTREAM 概觀](http://go.microsoft.com/fwlink/?LinkId=115291)。  
  
<a name="BinarySerialization"></a>   
### 二進位序列化  
 如果某個類別實作 <xref:System.Runtime.Serialization.ISerializable> 介面，您就可以將物件序列化成任何 SQL 二進位欄位 \(`BINARY`、`VARBINARY` 或 `IMAGE`\)。  此物件會根據 <xref:System.Runtime.Serialization.ISerializable> 介面的實作方式序列化和還原序列化。  如需詳細資訊，請參閱[二進位序列化](http://go.microsoft.com/fwlink/?LinkId=115581)。  
  
<a name="MiscMapping"></a>   
## 其他對應  
 下表顯示尚未提及之某些其他型別的預設型別對應。  下表顯示根據資料庫建置物件模型或外部對應檔案時，O\/R 設計工具和 SQLMetal 所選取的 CLR 型別。  
  
|SQL Server 型別|O\/R 設計工具和 SQLMetal 所使用的預設 CLR 型別對應|  
|-------------------|-----------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=fullName>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=fullName>|  
  
 下表顯示 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 方法用於定義建立哪些 SQL 資料行型別來對應至 CLR 型別 \(定義於物件模型或外部對應檔案中\) 的預設型別對應。  
  
|CLR 型別|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 所使用的預設 SQL Server 型別|  
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=fullName>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=fullName>|`SQL_VARIANT`|  
  
 LINQ to SQL 不支援這些其他型別的任何其他型別對應。  如需詳細資訊，請參閱[型別對應的執行階段行為對照表](#BehaviorMatrix)。  
  
## 請參閱  
 [以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [SQL\-CLR 類型不符](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)