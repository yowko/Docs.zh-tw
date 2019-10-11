---
title: XmlSchemaValidator 推入型驗證
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a420a134eda6c62758b0d218e3c0a4a4922b048c
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250049"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator 推入型驗證

<xref:System.Xml.Schema.XmlSchemaValidator> 類別提供有效率的高效能機制，可根據 XML 結構描述以推入方式驗證 XML 資料。 例如，<xref:System.Xml.Schema.XmlSchemaValidator> 類別可讓您就地驗證 XML 資訊集，而無需將其序列化為 XML 文件，然後使用驗證 XML 讀取器重新剖析該文件。

<xref:System.Xml.Schema.XmlSchemaValidator> 類別可用於進階案例中，如建置自訂 XML 資料來源的驗證引擎，或做為建置驗證 XML 寫入器的一種方式。

以下是使用 <xref:System.Xml.Schema.XmlSchemaValidator> 類別，根據 `contosoBooks.xml` 結構描述驗證 `contosoBooks.xsd` 檔案的範例。 此範例使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將 `contosoBooks.xml` 檔案還原序列化，並將節點的值傳遞給 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的方法。

> [!NOTE]
> 此範例用於本主題的各節中。

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

該範例採用 `contosoBooks.xml` 檔案做為輸入。

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

該範例還採用 `contosoBooks.xsd` 做為輸入。

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="bookstore">
        <xs:complexType>
            <xs:sequence>
                <xs:element maxOccurs="unbounded" name="book">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="title" type="xs:string" />
                            <xs:element name="author">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element minOccurs="0" name="name" type="xs:string" />
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />
                                    </xs:sequence>
                                </xs:complexType>
                            </xs:element>
                            <xs:element name="price" type="xs:decimal" />
                        </xs:sequence>
                        <xs:attribute name="genre" type="xs:string" use="required" />
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />
                        <xs:attribute name="ISBN" type="xs:string" use="required" />
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

## <a name="validating-xml-data-using-xmlschemavalidator"></a>使用 XmlSchemaValidator 驗證 XML 資料

若要開始驗證 XML 資訊集，您必須先使用 <xref:System.Xml.Schema.XmlSchemaValidator> 建構函式初始化 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 類別的新執行個體。

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式以 <xref:System.Xml.XmlNameTable>、<xref:System.Xml.Schema.XmlSchemaSet> 及 <xref:System.Xml.XmlNamespaceManager>物件做為參數，並以 <xref:System.Xml.Schema.XmlSchemaValidationFlags> 值做為參數。 <xref:System.Xml.XmlNameTable> 物件可用於儘量縮減已知命名空間字串 (如結構描述命名空間、XML 命名空間等)，並在驗證簡單內容期間，將其傳遞給 <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> 方法。 <xref:System.Xml.Schema.XmlSchemaSet> 物件包含用於驗證 XML 資訊集的 XML 結構描述。 <xref:System.Xml.XmlNamespaceManager> 物件可用於解析驗證期間遇到的命名空間。 <xref:System.Xml.Schema.XmlSchemaValidationFlags> 可用於停用某些驗證功能。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

### <a name="initializing-validation"></a>初始化驗證

建構 <xref:System.Xml.Schema.XmlSchemaValidator> 物件之後，可以採用兩種多載 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的狀態。 以下是這兩個 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法。

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為其開始狀態，以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 做為參數的多載 <xref:System.Xml.Schema.XmlSchemaObject> 方法，會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為開始狀態，以進行部分驗證。

只有在建構 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 物件或呼叫 <xref:System.Xml.Schema.XmlSchemaValidator> 之後，才可立即呼叫這兩種 <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> 方法。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法的範例，請參閱簡介中的範例。 如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

#### <a name="partial-validation"></a>部分驗證

以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 做為參數的 <xref:System.Xml.Schema.XmlSchemaObject> 方法會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為開始狀態，以進行部分驗證。

在下列範例中，會使用 <xref:System.Xml.Schema.XmlSchemaObject> 方法初始化用於部分驗證的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>。 傳遞 `orderNumber` 結構描述項目的方法是，在 <xref:System.Xml.XmlQualifiedName> 物件之 <xref:System.Xml.Schema.XmlSchemaObjectTable> 屬性所傳回的 <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> 集合中，依 <xref:System.Xml.Schema.XmlSchemaSet> 選取結構描述項目。 然後，<xref:System.Xml.Schema.XmlSchemaValidator> 物件會驗證此特定項目。

```vb
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
schemaSet.Compile()
Dim nameTable As NameTable = New NameTable()
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)

Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))

validator.ValidateElement("orderNumber", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateText("123")
validator.ValidateEndElement(Nothing)
```

```csharp
XmlSchemaSet schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
schemaSet.Compile();
NameTable nameTable = new NameTable();
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);

XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);

validator.ValidateElement("orderNumber", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateText("123");
validator.ValidateEndElement(null);
```

該範例使用下列 XML 結構描述做為輸入。

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

### <a name="adding-additional-schemas"></a>加入其他結構描述

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別的 <xref:System.Xml.Schema.XmlSchemaValidator> 方法，可用於在驗證期間將 XML 結構描述加入至一組結構描述。 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法可用於模擬在要驗證之 XML 資訊集中遇到內嵌 XML 結構描述時的效果。

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchema> 參數的目標命名空間與 <xref:System.Xml.Schema.XmlSchemaValidator> 物件已遇到之任何項目或屬性的目標命名空間均不相符。
>
> 如果未將 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> 值做為參數傳遞給 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式，則 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法將不起作用。

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的結果取決於要驗證的目前 XML 節點內容。 如需驗證內容的詳細資訊，請參閱本主題的＜驗證內容＞一節。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

### <a name="validating-elements-attributes-and-content"></a>驗證項目、屬性及內容

<xref:System.Xml.Schema.XmlSchemaValidator> 類別提供幾種方法，可用於根據 XML 結構描述驗證 XML 資訊集中的項目、屬性及內容。 下表對每個方法進行說明。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|驗證目前內容中的項目名稱。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|驗證目前項目內容中的屬性，或根據做為參數傳遞給 <xref:System.Xml.Schema.XmlSchemaAttribute> 方法的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 物件驗證屬性。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|驗證項目內容中的所有必要屬性是否均已存在，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件以驗證項目的子內容。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|驗證目前項目內容中是否允許文字，並且累積文件以驗證目前項目是否有簡單內容。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|驗證目前項目內容中是否允許泛空白字元，並且累積泛空白字元以驗證目前項目是否有簡單內容。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|對於含簡單內容的項目，根據其資料型別驗證項目的文字內容是否有效；對於含複雜內容的項目，驗證目前項目的內容是否完整。|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|略過目前項目內容的驗證，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件，以驗證父項目內容 (Context) 中的內容 (Content)。|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|結束驗證，並且若已設定 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> 驗證選項，則檢查整個 XML 文件的識別條件約束。|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> 類別具有定義的狀態轉換，可強制轉換對前一表格中說明之每個方法的呼叫順序及次數。 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的特定狀態轉換，在本主題的＜XmlSchemaValidator 狀態轉換＞一節中加以說明。

如需用來驗證 XML 資訊集中項目、屬性及內容之方法的範例，請參閱前一節中的範例。 如需這些方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

#### <a name="validating-content-using-an-xmlvaluegetter"></a>使用 XmlValueGetter 驗證內容

<xref:System.Xml.Schema.XmlValueGetter>`delegate` 可用於傳遞屬性、文字或泛空白字元節點的值，成為 Common Language Runtime (CLR) 型別，該型別與它們的 XML 結構描述定義語言 (XSD) 型別相容。 如果屬性、文字或泛空白字元節點的 CLR 值已經可用，則 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 就很有用，且避免將它轉換為 `string`，然後重新剖析以進行驗證的成本。

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> 方法是多載方法，並可接受屬性、文字及泛空白字元節點的值做為 `string` 或 <xref:System.Xml.Schema.XmlValueGetter>`delegate`。

<xref:System.Xml.Schema.XmlSchemaValidator> 類別的下列方法接受 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 做為參數。

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

以下 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 範例取自簡介中的 <xref:System.Xml.Schema.XmlSchemaValidator> 類別範例。 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 會將屬性的值做為 <xref:System.DateTime> 物件傳回。 為驗證 <xref:System.DateTime> 傳回的 <xref:System.Xml.Schema.XmlValueGetter> 物件，<xref:System.Xml.Schema.XmlSchemaValidator> 物件先將其轉換成屬性資料型別 ValueType (ValueType 是 XSD 型別的預設 CLR 對應)，然後檢查已轉換值的 Facet。

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

如需 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 的完整範例，請參閱簡介中的範例。 如需 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlValueGetter> 及 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

#### <a name="post-schema-validation-information"></a>Post-Schema-Validation-Information

<xref:System.Xml.Schema.XmlSchemaInfo> 類別表示 <xref:System.Xml.Schema.XmlSchemaValidator> 類別所驗證之 XML 節點的部分後結構描述驗證資訊。 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的各種方法均可以接受 <xref:System.Xml.Schema.XmlSchemaInfo> 物件做為選擇性 (`null`) `out` 參數。

成功驗證後，會以驗證的結果設定 <xref:System.Xml.Schema.XmlSchemaInfo> 物件的屬性。 例如，使用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法成功驗證屬性後，會以驗證的結果設定 <xref:System.Xml.Schema.XmlSchemaInfo> 物件的 (如果已指定) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> 及 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 屬性。

下列 <xref:System.Xml.Schema.XmlSchemaValidator> 類別方法接受 <xref:System.Xml.Schema.XmlSchemaInfo> 物件做為輸出參數。

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

如需 <xref:System.Xml.Schema.XmlSchemaInfo> 類別的完整範例，請參閱簡介中的範例。 如需 <xref:System.Xml.Schema.XmlSchemaInfo> 類別的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaInfo> 類別參考文件。

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>擷取預期物件、屬性及未指定的預設屬性

<xref:System.Xml.Schema.XmlSchemaValidator> 類別提供 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，以擷取目前驗證內容中的預期物件、屬性及未指定的預設屬性。

#### <a name="retrieving-expected-particles"></a>擷取預期物件

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回含目前項目內容中預期物件 (Particle) 的 <xref:System.Xml.Schema.XmlSchemaParticle> 物件 (Object) 陣列。 可由 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法傳回的有效物件為 <xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaAny> 類別的執行個體。

當內容模型的複合器為 `xs:sequence` 時，只傳回序列中的下一個物件。 如果內容模型的複合器為 `xs:all` 或 `xs:choice`，則傳回目前項目內容中所有後續的有效物件。

> [!NOTE]
> 如果在呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法後立即呼叫<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回所有的全域項目。

例如，在隨後的 XML 結構描述定義語言 (XSD) 結構描述及 XML 文件中，驗證 `book` 項目之後，`book` 項目會成為目前的項目內容。 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaElement> 物件的陣列，該物件表示 `title` 項目。 當驗證內容為 `title` 項目時，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回空陣列。 如果在驗證 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 項目之後、驗證 `title` 項目之前，呼叫 `description` 方法，則它會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaElement> 物件的陣列，該物件表示 `description` 項目。 如果在驗證 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 項目之後呼叫 `description` 方法，則它會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaAny> 物件的陣列，該物件表示萬用字元。

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
validator.Initialize()

validator.ValidateElement("book", "", Nothing)

validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("title", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next
validator.ValidateEndElement(Nothing)

For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("description", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()
    Console.WriteLine(particle.GetType())
Next

validator.ValidateElement("namespace", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

validator.ValidateEndElement(Nothing)
```

```csharp
XmlReader reader = XmlReader.Create("input.xml");

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize();

validator.ValidateElement("book", "", null);

validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("title", "", null);
validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}
validator.ValidateEndElement(null);

foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("description", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())
{
    Console.WriteLine(particle.GetType());
}

validator.ValidateElement("namespace", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

validator.ValidateEndElement(null);
```

 此範例會使用下列 XML 做為輸入：

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

此範例會採用下列 XSD 架構做為輸入：

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。 如需詳細資訊，請參閱本主題的＜驗證內容＞一節。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的範例，請參閱簡介中的範例。 如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

#### <a name="retrieving-expected-attributes"></a>擷取預期屬性

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法會傳回含目前項目內容中預期屬性的 <xref:System.Xml.Schema.XmlSchemaAttribute> 物件陣列。

例如，在簡介內的範例中，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法用於擷取 `book` 項目的所有屬性。

如果在呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法之後立即呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> 方法，則會傳回 XML 文件中出現的所有屬性。 但是，如果在對 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法進行一或多次呼叫之後呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法，則會傳回目前項目之尚未驗證的屬性。

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。 如需詳細資訊，請參閱本主題的＜驗證內容＞一節。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的範例，請參閱簡介中的範例。 如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

#### <a name="retrieving-unspecified-default-attributes"></a>擷取未指定的預設屬性

對於項目內容中其預設值尚未使用 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法加以驗證的任何屬性，<xref:System.Collections.ArrayList> 方法以 <xref:System.Xml.Schema.XmlSchemaAttribute> 物件填入指定的 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>。 應先在項目內容中的每個屬性上呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，再呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法。 應使用 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，判斷要將哪些預設屬性插入要驗證的 XML 文件。

如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。

### <a name="handling-schema-validation-events"></a>處理結構描述驗證事件

<xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> 類別的 <xref:System.Xml.Schema.XmlSchemaValidator> 事件會處理驗證期間發生的結構描述驗證警告及錯誤。

結構描述驗證警告的 <xref:System.Xml.Schema.XmlSeverityType> 值為 <xref:System.Xml.Schema.XmlSeverityType.Warning>；結構描述驗證錯誤的 <xref:System.Xml.Schema.XmlSeverityType> 值為 <xref:System.Xml.Schema.XmlSeverityType.Error>。 如果尚未指派 <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>，則會針對 <xref:System.Xml.Schema.XmlSchemaValidationException> 值為 <xref:System.Xml.Schema.XmlSeverityType> 的所有結構描述驗證錯誤，擲回 <xref:System.Xml.Schema.XmlSeverityType.Error>。 但是，對於 <xref:System.Xml.Schema.XmlSchemaValidationException> 值為 <xref:System.Xml.Schema.XmlSeverityType> 的結構描述驗證警告，則不會擲回 <xref:System.Xml.Schema.XmlSeverityType.Warning>。

以下內容取自簡介中，擷取結構描述驗證期間發生之結構描述驗證警告及錯誤的 <xref:System.Xml.Schema.ValidationEventHandler> 範例。

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

    Select Case e.Severity
        Case XmlSeverityType.Error
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)
            Exit Sub
        Case XmlSeverityType.Warning
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)
            Exit Sub
    End Select
End Sub
```

```csharp
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)
{
    switch (e.Severity)
    {
        case XmlSeverityType.Error:
            Console.WriteLine("\nError: {0}", e.Message);
            break;
        case XmlSeverityType.Warning:
            Console.WriteLine("\nWarning: {0}", e.Message);
            break;
    }
}
```

如需 <xref:System.Xml.Schema.ValidationEventHandler> 的完整範例，請參閱簡介中的範例。 如需詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaInfo> 類別參考文件。

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator 狀態轉換

<xref:System.Xml.Schema.XmlSchemaValidator> 類別具有定義的狀態轉換，可強制轉換用於驗證 XML 資訊集內項目、屬性及內容之每個方法的呼叫順序及次數。

下表說明 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的狀態轉換，以及在每個狀態下可進行之方法呼叫的順序及次數。

|State|轉換|
|-----------|----------------|
|Validate|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; 項目|
|元素|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;|
|內容|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; 項目|

> [!NOTE]
> 根據 <xref:System.InvalidOperationException> 物件的目前狀態，如果呼叫上表中的每個方法的順序不正確，則它們會擲回 <xref:System.Xml.Schema.XmlSchemaValidator>。

以上狀態轉換表會使用標點符號，說明可針對 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之狀態轉換的每個狀態呼叫的方法及其他狀態。 所使用的符號與在物件型別定義 (DTD) 之 XML 標準參考中找到的符號相同。

下表說明在以上狀態轉換表中找到的標點符號，如何影響針對 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之狀態轉換中每個狀態呼叫的方法及其他狀態。

|符號|描述|
|------------|-----------------|
|&#124;|可呼叫方法或狀態 (垂直線前後的項目)。|
|?|問號之前的方法或狀態是選擇性的，但如果呼叫它，則只能呼叫一次。|
|*|\* 符號之前的方法或狀態是選擇性的，可對其呼叫多次。|

## <a name="validation-context"></a>驗證內容

用於驗證 XML 資訊集中項目、屬性及內容之 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的方法，可變更 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的驗證內容。 例如，<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> 方法會略過目前項目內容的驗證，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件以驗證父項目內容 (Context) 中的內容 (Content)；這相當於略過目前項目之所有項目子系的驗證，並呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 方法。

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。

下表說明在呼叫用於驗證 XML 資訊集中項目、屬性及內容之 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的其中一個方法之後，呼叫這些方法的結果。

|方法|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|如果呼叫預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回包含所有全域項目的陣列。<br /><br /> 如果呼叫以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 做為參數之多載 <xref:System.Xml.Schema.XmlSchemaObject> 方法，以初始化項目的部分驗證，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 僅會傳回已初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的項目。|如果呼叫預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。<br /><br /> 如果呼叫以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 做為參數之 <xref:System.Xml.Schema.XmlSchemaObject> 方法的多載，以初始化屬性的部分驗證，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 僅會傳回已初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的屬性。|如果結構描述未發生前置處理錯誤，則將其加入 <xref:System.Xml.Schema.XmlSchemaSet> 物件的<xref:System.Xml.Schema.XmlSchemaValidator>。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|如果內容項目有效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之項目子系的項目序列。<br /><br /> 如果內容項目無效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。|如果內容項目有效，且先前並未呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>，則<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回內容項目上定義之所有屬性的清單。<br /><br /> 如果已驗證部分屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之其餘屬性的清單。<br /><br /> 如果內容項目無效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|如果內容屬性是最上層屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。<br /><br /> 否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。|如果內容屬性是最上層屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。<br /><br /> 否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之其餘屬性的清單。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之內容項目的必要及選擇性屬性清單。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|如果內容項目的 contentType 為 Mixed，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回下一個位置中預期的項目序列。<br /><br /> 如果內容項目的 contentType 為 TextOnly 或 Empty，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。<br /><br /> 如果內容項目的 contentType 為 ElementOnly，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回下一個位置中預期的、但已發生驗證錯誤的項目序列。|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回未驗證之屬性的內容項目清單。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|如果內容泛空白字元是最上層泛空白字元，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。<br /><br /> 否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的行為與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中的相同。|如果內容泛空白字元是最上層泛空白字元，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。<br /><br /> 否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的行為與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中的相同。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期位於內容項目之後 (可能為同層級) 的項目序列。|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回未驗證之屬性的內容項目清單。<br /><br /> 如果內容項目沒有父代，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空清單 (內容項目是已呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 之目前項目的父代)。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。|與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。|同上。|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|傳回空陣列。|傳回空陣列。|同上。|

> [!NOTE]
> 呼叫上表中的任何方法，均不會改變 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之各種屬性所傳回的值。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Schema.XmlSchemaValidator>
