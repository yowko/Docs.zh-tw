---
title: Entity Framework 詞彙
ms.date: 03/30/2017
ms.assetid: fa2a1bd1-6118-487b-8673-eebc66b92945
ms.openlocfilehash: c48361fd51ecb320416e76e599e36da12faf76fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854283"
---
# <a name="entity-framework-terminology"></a>Entity Framework 詞彙
本主題定義 Entity Framework 檔中經常參考的詞彙。 而為相關主題提供的連結表示有其他可用的資訊。  
  
|詞彙|定義|  
|----------|----------------|  
|關聯|實體類型間的關聯性定義。<br /><br /> 如需詳細資訊，請參閱[Association 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#association-element-csdl)和[關聯類型](../association-type.md)。|  
|Association Set - 關聯集|用於相同類型之關聯執行個體的邏輯容器。<br /><br /> 如需詳細資訊，請參閱[AssociationSet 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#associationset-element-csdl)和[關聯集](../association-set.md)。|  
|Code First|從 Entity Framework 4.1 開始，您可以使用 Code First 開發透過程式設計方式建立模型。 Code First 開發有兩種不同的方案。 在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。<br /><br /> 請注意，Code First 的開發是[Entity Framework 5.0](https://go.microsoft.com/fwlink/?LinkId=234900)的一部分。 Entity Framework 5.0 不是 .NET Framework 的一部分，而是建置在 .NET Framework 4.5 之上。 Entity Framework 5.0 是以[Entity Framework](https://go.microsoft.com/fwlink/?LinkID=215714) [NuGet](https://go.microsoft.com/fwlink/?LinkId=232488)套件的形式提供。 如需詳細資訊，請參閱[Entity Framework 版本和版本控制](https://go.microsoft.com/fwlink/?LinkId=234899)。|  
|Command Tree - 命令樹|所有由一或多個運算式組成之 Entity Framework 查詢的通用、程式設計標記法。<br /><br /> 如需詳細資訊，請參閱[Entity Framework 總覽](overview.md)。|  
|複雜類型|.NET Framework 類別，表示概念模型中所定義的複雜屬性。 複雜類型可使純量屬性在實體內有組織結構。 複雜物件是複雜類型的執行個體。 如需詳細資訊，請參閱[ComplexType 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#complextype-element-csdl)和[複雜類型](../complex-type.md)。|  
|ComplexType|資料型別的規格，其中表示實體類型的非純量屬性沒有索引鍵屬性。<br /><br /> 如需詳細資訊，請參閱[ComplexType 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#complextype-element-csdl)和[複雜類型](../complex-type.md)。|  
|概念模型|Entity Framework 中應用程式的網域中，實體類型、複雜類型、關聯、實體容器、實體集和關聯集的抽象規格。 概念模型是以 CSDL 定義於 .csdl 檔案。<br /><br /> 如需詳細資訊，請參閱[模型化和對應](modeling-and-mapping.md)。|  
|.csdl file - .csdl 檔案|包含概念模型的 XML 檔案 (以 CSDL 表示)。|  
|概念結構描述定義語言 (CSDL)|XML 架構的語言，可用來定義概念性模型的實體類型、關聯、實體容器、實體集以及關聯集。<br /><br /> 如需詳細資訊，請參閱 [CSDL Specification](./language-reference/csdl-specification.md)。|  
|Container - 容器|實體集和關聯集的邏輯群組。<br /><br /> 如需詳細資訊，請參閱[EntityContainer 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitycontainer-element-csdl)和[實體容器](../entity-container.md)。|  
|並行|讓多個使用者同時存取和變更共用資料的程序。 根據預設，Entity Framework 會實行開放式平行存取模型。|  
|方向|參考某些關聯的非對稱性質。 方向在結構描述內是與 `FromRole` 或 `ToRole` 項目的 `NavigationProperty` 和 `ReferentialConstraint` 屬性一起指定。<br /><br /> 如需詳細資訊，請參閱[NavigationProperty 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#navigationproperty-element-csdl)和[導覽屬性](../navigation-property.md)。|  
|Eager Loading - 立即載入|載入特定的相關物件組之程序，會連同查詢中所明確要求的物件一起載入。|  
|.edmx 檔案|XML 檔案，內含概念模型 (以 CSDL 表示)、儲存體模型 (以 SSDL 表示) 和兩種模型之間的對應 (以 MSL 表示)。 .Edmx 檔案是由實體資料模型工具所建立。 如需詳細資訊，請參閱[.edmx 檔案總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))。|  
|end|參與關聯的實體。<br /><br /> 如需詳細資訊，請參閱[End Element （CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)和[association end](../association-end.md)。|  
|實體|在定義資料型別的應用程式定義域中的概念。<br /><br /> 如需詳細資訊，請參閱[EntityType 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitytype-element-csdl)和[實體類型](../entity-type.md)。|  
|EntityClient|與儲存體無關的 ADO.NET 資料提供者，其中包含`EntityConnection`、 `EntityCommand`和`EntityDataReader`之類的類別。 使用[!INCLUDE[esql](../../../../../includes/esql-md.md)]並連接至儲存體特定的 ADO.NET 資料提供者， `SqlClient`例如。<br /><br /> 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)。|  
|Entity Container - 實體容器|指定將實作於指定之命名空間中的實體集和關聯集。<br /><br /> 如需詳細資訊，請參閱[EntityContainer 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitycontainer-element-csdl)和[實體容器](../entity-container.md)。|  
|實體資料模型 (EDM)|描述資料結構的概念集，就像實體和關聯性一樣，不論其儲存形式為何。<br /><br /> 如需詳細資訊，請參閱[實體資料模型](../entity-data-model.md)。|  
|Entity Framework|一組藉由讓開發人員使用對應至資料來源中邏輯結構描述的概念模型，進而可以支援資料導向軟體應用程式開發的技術。<br /><br /> 如需詳細資訊，請參閱[Entity Framework 總覽](overview.md)。|  
|實體集|用於所指型別及其子型別之實體的邏輯容器。 實體集在資料庫中是對應至資料表。<br /><br /> 如需詳細資訊，請參閱[EntitySet 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entityset-element-csdl)和[實體集](../entity-set.md)。|  
|Entity SQL|與儲存體無關的 SQL Dialect，可直接與概念實體結構描述一起運作並支援概念模型的概念，例如繼承和關聯性。<br /><br /> 如需詳細資訊，請參閱[Entity SQL 語言](./language-reference/entity-sql-language.md)。|  
|Entity Type - 實體類型|代表概念模型中所定義之實體的 .NET Framework 類別。 實體類型可以有純量、複雜和導覽屬性。 物件是實體類型的執行個體。 如需詳細資訊，請參閱[使用物件](working-with-objects.md)。|  
|EntityType|資料型別的規格，其中包括索引鍵和一組具名屬性以及表示概念模型或儲存體模型中的最上層項目。<br /><br /> 如需詳細資訊，請參閱[EntityType 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitytype-element-csdl)和[實體類型](../entity-type.md)。|  
|Explicit Loading - 明確載入|當查詢傳回物件時，相關物件不會同時載入。 根據預設，在導覽屬性上使用 `Load` 方法明確要求之前，不會載入相關物件。|  
|Foreign Key Association - 外部索引鍵關聯|實體間的關聯，透過外部索引鍵屬性加以管理。|  
|Identifying Relationship - 識別關聯性|一種關聯性，其中主要實體的主索引鍵也是相依實體之主索引鍵的一部分。 在這種關聯性中，如果沒有主要實體，相依實體就無法存在。|  
|Independent Association - 獨立關聯|實體間的關聯，透過獨立物件加以表示及追蹤。|  
|key|實體類型的屬性，其中指定要用來識別實體類型之唯一執行個體的屬性或屬性集。 它是由 <xref:System.Data.EntityKey> 類別顯示在物件層。<br /><br /> 如需詳細資訊，請參閱[Key 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#key-element-csdl)和[實體索引鍵](../entity-key.md)。|  
|消極式載入|當查詢傳回物件時，相關物件不會同時載入。 反而是存取導覽屬性時會自動載入相關的物件。|  
|LINQ to Entities|定義一組查詢運算子的查詢語法，可讓您在視覺效果C#和 Visual Basic 中以直接宣告的方式表示進行遍歷、篩選和投射作業。<br /><br /> 如需詳細資訊，請參閱[LINQ to Entities](./language-reference/linq-to-entities.md)。|  
|對應|概念模型中的項目與儲存體模型中項目之間的對應規格。<br /><br /> 如需詳細資訊，請參閱[MSL 規格](./language-reference/msl-specification.md)。|  
|.msl file - .msl 檔案|XML 檔案，內含概念模型及儲存體模型之間的對應 (以 MSL 表示)。|  
|對應規格語言 (MSL)|一種 XML 架構語言，用來將定義於概念性模型中的項目對應到儲存體模型中的項目。<br /><br /> 如需詳細資訊，請參閱[MSL 規格](./language-reference/msl-specification.md)。|  
|Modification Function - 修改函式|用於插入、更新和刪除資料來源中之資料的預存程序。 這些函數可用來取代產生的 Entity Framework 命令。 修改函式是由儲存體模型中的 `Function` 項目來定義。 [ModificationFunctionMapping](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716778(v=vs.100))元素會針對概念模型中定義的實體，將這些修改函數對應至插入、更新和刪除作業。|  
|多重性|可存在於關聯性各端的實體數 (依關聯定義)。 多重性也可稱為基數。<br /><br /> 如需詳細資訊，請參閱[End Element （CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)和[association end](../association-end.md)。|  
|Multiple Entity Sets Per Type - 每個類型的多重實體|在多個實體集內定義實體類型的能力。<br /><br /> 如需詳細資訊，請參閱[EntitySet 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entityset-element-csdl)和[如何：針對每個類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738537(v=vs.100))定義具有多個實體集的模型。|  
|導覽屬性|表示與另一個實體類型之關聯性的實體類型屬性 (依關聯定義)。 導覽屬性是用來傳回相關物件做為 <xref:System.Data.Objects.DataClasses.EntityCollection%601> 或 <xref:System.Data.Objects.DataClasses.EntityReference%601> (視關聯另一端的多重性而定)。<br /><br /> 如需詳細資訊，請參閱[NavigationProperty 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#navigationproperty-element-csdl)和[導覽屬性](../navigation-property.md)。|  
|Query Path - 查詢路徑|路徑的字串表示，其中指定在執行物件查詢時要傳回的相關物件。 查詢路徑是由在 <xref:System.Data.Objects.ObjectQuery%601.Include%2A> 上呼叫 <xref:System.Data.Objects.ObjectQuery%601> 方法來定義。<br /><br /> 如需詳細資訊，請參閱[載入相關物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))。|  
|物件內容|表示概念模型中定義的實體容器。 它會包含基礎資料來源的連接並提供如變更追蹤和識別解析這類的服務。 物件內容是由 <xref:System.Data.Objects.ObjectContext> 或 `DbContext` 類別的執行個體來表示。<br /><br /> `DbContext`是[Entity Framework 5.0](https://go.microsoft.com/fwlink/?LinkId=234900)的一部分。 Entity Framework 5.0 不是 .NET Framework 的一部分，而是建置在 .NET Framework 4.5 之上。 Entity Framework 5.0 是以[Entity Framework](https://go.microsoft.com/fwlink/?LinkID=215714) [NuGet](https://go.microsoft.com/fwlink/?LinkId=232488)套件的形式提供。 如需詳細資訊，請參閱[Entity Framework 版本和版本控制](https://go.microsoft.com/fwlink/?LinkId=234899)。|  
|Object Layer - 物件層|Entity Framework 所使用的實體類型和內容物件定義。|  
|Object Query - 物件查詢|在物件內容中針對概念模型執行的查詢，該物件內容會傳回資料做為物件。<br /><br /> 如需詳細資訊，請參閱[物件查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))。|  
|Object-Relational Mapping - 物件關聯式對應|將資料從關聯式資料庫轉換成資料型別的技巧，該資料型別可在物件導向軟體應用程式中使用。<br /><br /> Entity Framework 提供物件關聯式對應服務，其方式是將關聯式資料（如儲存模型中所定義）對應到概念模型中所定義的資料類型。<br /><br /> 如需詳細資訊，請參閱[模型化和對應](modeling-and-mapping.md)。|  
|物件服務|Entity Framework 所提供的服務，可讓應用程式程式碼在 .NET Framework 物件之類的實體上運作。|  
|Persistence-Ignorant Object - 非持續性物件|不包含任何與資料儲存體相關之邏輯的物件。 也可稱為 POCO 實體。|  
|POCO|Plain Old CLR Object - 簡單的 CLR 物件。 不會繼承自另一類別或實作介面的物件。|  
|POCO entity - POCO 實體|Entity Framework 中的實體不會繼承自<xref:System.Data.Objects.DataClasses.EntityObject>或<xref:System.Data.Objects.DataClasses.ComplexObject> ，而且不會執行 Entity Framework 介面。 POCO 實體通常是您在 Entity Framework 應用程式中使用的現有網域物件。 這些實體支援非持續性。 如需詳細資訊，請參閱[使用 POCO 實體](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100))。|  
|proxy object - Proxy 物件|衍生自 POCO 類別的物件，由 Entity Framework 所產生，以支援變更追蹤和消極式載入。 如需詳細資訊，請參閱[建立 POCO](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd468057(v=vs.100))Proxy 的需求。|  
|Referential Constraint - 參考條件約束|概念模型中定義的條件約束，指出實體與另一個實體之間有相依關聯性。 這種限制式表示若無準則實體的對應執行個體，則相依實體的執行個體無法存在。<br /><br /> 如需詳細資訊，請參閱[ReferentialConstraint 元素（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#referentialconstraint-element-csdl)和[參考完整性條件約束](../referential-integrity-constraint.md)。|  
|Relationship - 關聯性|實體間的邏輯連接。|  
|角色 (role)|指定給關聯的每個 `End` 的名稱，以釐清關聯性的語意。<br /><br /> 如需詳細資訊，請參閱[End Element （CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)和[association end](../association-end.md)。|  
|Scalar Property - 純量屬性|對應至儲存體模型中單一欄位的實體屬性。|  
|Self-Tracking Entity - 自我追蹤實體|根據「文字範本轉換工具組」(Text Template Transformation Toolkit，T4) 建置而成的實體，這種實體能夠記錄純量、複雜和導覽屬性的變更。|  
|Simple Type - 簡單型別|用於定義概念模型中屬性的基本型別 (Primitive Type)。<br /><br /> 如需詳細資訊，請參閱[概念模型類型（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)和[實體資料模型：基本資料類型](../entity-data-model-primitive-data-types.md)。|  
|Split Entity - 分割實體|對應至儲存體模型中兩個不同類型的實體類型。<br /><br /> 如需詳細資訊，請參閱[如何：定義一個模型，其中包含對應至兩個數據表](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896233(v=vs.100))的單一實體。|  
|儲存體模型|支援的資料來源 (如關聯式資料庫) 中資料邏輯模型的定義。 儲存體模型在 .ssdl 檔案中是以 SSDL 定義的。<br /><br /> 如需詳細資訊，請參閱[模型化和對應](modeling-and-mapping.md)和[SSDL 規格](./language-reference/ssdl-specification.md)。|  
|.ssdl file - .ssdl 檔案|內含儲存體模型的 XML 檔案 (以 SSDL 表示)。|  
|存放區結構描述定義語言 (SSDL)|以 XML 為架構的語言，用於定義儲存體模型 (通常相當於資料庫結構描述) 的實體類型、關聯、實體容器、實體集和關聯集。<br /><br /> 如需詳細資訊，請參閱[SSDL 規格](./language-reference/ssdl-specification.md)。|  
|單表|一種將資料庫內某個類型階層架構模型化的方法，此方法會將階層架構中所有類型的屬性都包含至一張資料表中。|  
|一類一表|一種將資料庫內某個類型階層架構模型化的方法，此方法會使用多個具有一對一關聯性的資料表來設定各種類型的模型。|  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](index.md)
- [Entity Framework 概觀](overview.md)
- [快速入門](getting-started.md)
- [Entity Framework 資源](resources.md)
