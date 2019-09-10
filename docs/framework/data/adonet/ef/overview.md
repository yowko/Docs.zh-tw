---
title: Entity Framework 概觀
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 92aa7b9c1f163c0496a821cca375c8b7e1b21a5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854350"
---
# <a name="entity-framework-overview"></a>Entity Framework 總覽

Entity Framework 是 ADO.NET 中的一組技術，可支援資料導向軟體應用程式的開發。 資料導向應用程式的架構設計人員和開發人員經常致力於滿足達成兩個迥異目標的需求。 他們必須針對所解決之商務問題的實體、關聯性和邏輯建立模型，而且也必須使用用來儲存和擷取資料的資料引擎。 這項資料可能會跨越多個儲存系統，而且每個系統都有自己的通訊協定 (Protocol)。即使是使用單一儲存系統的應用程式都必須在儲存系統的需求與撰寫有效率和可維護應用程式程式碼的需求之間取得平衡。

此 Entity Framework 可讓開發人員以網域特定物件和屬性（例如客戶和客戶位址）的形式來使用資料，而不需要顧慮其本身的基礎資料庫資料表和資料行。儲存. 有了 Entity Framework，開發人員在處理資料時可以在較高的抽象層級工作，而且能夠使用比傳統應用程式更少的程式碼來建立及維護資料導向應用程式。 由於 Entity Framework 是 .NET Framework 的元件，因此 Entity Framework 應用程式可以在已安裝 3.5 SP1 開始之 .NET Framework 的任何電腦上執行。

## <a name="give-life-to-models"></a>將生命週期提供給模型
 傳統且常見的建置應用程式或服務之設計方式是將應用程式或服務分成三個部分：領域模型、邏輯模型和實體模型。 網域模型會在建立模型的系統中定義實體和關聯性。 關聯式資料庫的邏輯模型會將實體和關聯性正規化成含有外部索引鍵條件約束的資料表。 實體模型會透過指定儲存詳細資料 (例如資料分割和索引)，處理特定資料引擎的功能。

 雖然資料庫管理員會調整實體模型來改善效能，不過撰寫應用程式程式碼的程式設計人員主要會透過撰寫 SQL 查詢和呼叫預存程序 (Stored Procedure)，限制他們自己使用邏輯模型。 網域模型通常會當做擷取和傳達應用程式需求的工具使用，而經常當做在專案早期階段中檢視和討論，然後放棄的惰性圖表使用。 許多開發小組會略過建立概念模型，而從指定關聯式資料庫中的資料表、資料行和索引鍵開始。

 Entity Framework 藉由讓開發人員能夠查詢領域模型中的實體和關聯性（稱為 Entity Framework 中的*概念*模型），同時依賴 Entity Framework 將這些作業轉譯為數據源，來提供模型的生命週期。–特定的命令。 如此，應用程式便不再受限於特定資料來源的硬式編碼相依性。

 使用 Code First 時，會將概念模型對應至程式碼中的儲存模型。 Entity Framework 可以根據物件類型和您所定義的其他設定來推斷概念模型。 對應中繼資料會在執行階段產生，並以您定義網域類型的方式與您在程式碼中提供的其他組態資訊為基礎。 Entity Framework 視中繼資料而定，視需要產生資料庫。 如需詳細資訊，請參閱[建立和對應概念模型](https://go.microsoft.com/fwlink/?LinkID=235382)。

 使用實體資料模型工具時，概念模型、儲存體模型和兩者之間的對應會以 XML 架構的結構描述來表示，並定義於具有對應副檔名的檔案中。

- 概念結構定義語言 (CSDL) 會定義概念模型。 CSDL 是[實體資料模型](../entity-data-model.md)的 Entity Framework 執行。 副檔名是 .csdl。

- 存放結構定義語言 (SSDL) 會定義儲存體模型，也稱為邏輯模型。 副檔名是 .ssdl。

- 對應規格語言檔案 (MSL) 會定義儲存體模型和概念模型之間的對應。 副檔名是 .msl。

儲存體模型和對應可依需要變更，不需要變更概念模型、資料類別或應用程式程式碼。 由於儲存模型是提供者特有的，所以您可以在各種資料來源中使用一致的概念模型。

Entity Framework 會使用這些模型和對應檔，針對概念模型中的實體和關聯性，建立、讀取、更新和刪除作業，以對資料來源中的對等作業進行。 Entity Framework 甚至支援將概念模型中的實體對應至資料來源中的預存程式。 如需詳細資訊，請參閱[CSDL、SSDL 和 MSL 規格](./language-reference/csdl-ssdl-and-msl-specifications.md)。

## <a name="map-objects-to-data"></a>將物件對應至資料
 物件導向程式設計會提出與資料儲存系統互動的挑戰。 雖然類別的組織經常會與關聯式資料庫資料表的組織鏡像，但是這個符合並不完美。 多個正規化資料表經常會對應到單一類別，而且經常會使用與資料表之間的關聯性不同的方式來表示類別之間的關聯性。 例如，若要表示銷售訂單的客戶，`Order` 類別可能會使用包含 `Customer` 類別執行個體之參考的屬性，但是資料庫中的 `Order` 資料表資料列包含外部索引鍵資料行 (或資料行組)，而且其值對應至 `Customer` 資料表中的主索引鍵值。 `Customer` 類別可能具有名為 `Orders` 的屬性，其中包含 `Order` 類別執行個體的集合，但是資料庫中的 `Customer` 資料表沒有任何可比較的資料行。 Entity Framework 為開發人員提供以這種方式表示關聯性的彈性，或在資料庫中呈現更緊密的模型關聯性。

 現有的方案已經嘗試只將物件導向的類別和屬性對應至關聯式資料表和資料行，藉以填補這個間距 (經常稱為「阻抗不相符」)。 Entity Framework 將邏輯模型中的關聯式資料表、資料行和外鍵條件約束對應至概念模型中的實體和關聯性，而不是採用這種傳統方法。 這樣做可以在定義物件和最佳化邏輯模型方面提供更大的彈性。 實體資料模型工具會根據概念模型產生可擴充的資料類別。 這些類別是可以使用開發人員所加入的其他成員所擴充的部分類別。 根據預設，針對特定概念模型所產生的類別會衍生自提供服務來將實體具體化為物件以及追蹤和儲存變更的基底類別 (Base Class)。 開發人員可以使用這些類別，將實體和關聯性當做經由關聯而相關的物件進行處理。 開發人員也可以自訂為概念模型產生的類別。 如需詳細資訊，請參閱[使用物件](working-with-objects.md)。

## <a name="access-and-change-entity-data"></a>存取和變更實體資料

Entity Framework 不只是另一個物件關聯式對應方案而已，它基本上是有關如何讓應用程式存取和變更表示成概念模型中之實體和關聯性的資料。 Entity Framework 會使用模型和對應檔中的資訊，將針對概念模型中表示之實體類型的物件查詢轉譯成資料來源特有的查詢。 查詢結果會具體化為 Entity Framework 所管理的物件。 Entity Framework 提供下列方法來查詢概念模型和傳回物件：

- LINQ to Entities。 針對查詢在概念模型中定義的實體類型，提供了語言整合式查詢（LINQ）支援。 如需詳細資訊，請參閱[LINQ to Entities](./language-reference/linq-to-entities.md)。

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. 與儲存體無關的 SQL 方言，可直接與概念模型中的實體搭配使用，並支援實體資料模型的概念。 [!INCLUDE[esql](../../../../../includes/esql-md.md)]適用于使用 EntityClient 提供者執行的物件查詢和查詢。 如需詳細資訊，請參閱[Entity SQL 總覽](./language-reference/entity-sql-overview.md)。

Entity Framework 包含 EntityClient 資料提供者。 這個提供者會管理連接、將實體查詢轉譯成資料來源特有的查詢，並傳回 Entity Framework 用來將實體資料具體化為物件的資料讀取器。 不需要物件具體化時，EntityClient 提供者也可以當做標準 ADO.NET 資料提供者使用，方法是讓應用程式執行 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢並且取用傳回的唯讀資料讀取器。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)。

下圖說明用於處理資料的 Entity Framework 架構：

![Entity Framework 架構圖](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

實體資料模型工具可以產生衍生自`System.Data.Objects.ObjectContext`或`System.Data.Entity.DbContext`的類別，其代表概念模型中的實體容器。 這個物件內容會提供追蹤變更以及管理識別 (Identity)、並行和關聯性的機能。 這個類別也會公開 (Expose) 可針對資料來源進行寫入、插入、更新和刪除作業的 `SaveChanges` 方法。 就像查詢一樣，這些變更是由系統自動產生的命令所進行，或由開發人員指定的預存程序所進行。

## <a name="data-providers"></a>資料提供者

`EntityClient`提供者會藉由存取概念實體和關聯性方面的資料，來擴充 ADO.NET 提供者模型。 它將執行使用 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 的查詢。 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 提供了可讓 `EntityClient` 與資料庫通訊的基礎查詢語言。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)。

Entity Framework 包含支援標準命令樹的更新 SqlClient Data Provider。 如需詳細資訊，請參閱[SqlClient for the Entity Framework](sqlclient-for-the-entity-framework.md)。

## <a name="entity-data-model-tools"></a>實體資料模型工具

與 Entity Framework 執行時間一起，Visual Studio 包含對應和模型工具。 如需詳細資訊，請參閱[模型化和對應](modeling-and-mapping.md)。

## <a name="learn-more"></a>進一步了解

若要深入瞭解 Entity Framework，請參閱：

[消費者入門](getting-started.md)-提供如何使用快速[入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))快速啟動並執行的相關資訊，其中顯示如何建立簡單的 Entity Framework 應用程式。

[Entity Framework 的術語](terminology.md)-定義實體資料模型和 Entity Framework 引進的許多詞彙，並用於 Entity Framework 檔。

[Entity Framework 資源](resources.md)-提供概念主題的連結，以及外部主題和資源的連結，以建立 Entity Framework 的應用程式。

## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](index.md)
