---
title: "XmlSchemaValidator 推入型驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60c2effea612a579b4c66b7c30243b785b86a263
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="864cc-102">XmlSchemaValidator 推入型驗證</span><span class="sxs-lookup"><span data-stu-id="864cc-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="864cc-103"><xref:System.Xml.Schema.XmlSchemaValidator> 類別提供有效率的高效能機制，可根據 XML 結構描述以推入方式驗證 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="864cc-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="864cc-104">例如，<xref:System.Xml.Schema.XmlSchemaValidator> 類別可讓您就地驗證 XML 資訊集，而無需將其序列化為 XML 文件，然後使用驗證 XML 讀取器重新剖析該文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="864cc-105"><xref:System.Xml.Schema.XmlSchemaValidator> 類別可用於進階案例中，如建置自訂 XML 資料來源的驗證引擎，或做為建置驗證 XML 寫入器的一種方式。</span><span class="sxs-lookup"><span data-stu-id="864cc-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="864cc-106">以下是使用 <xref:System.Xml.Schema.XmlSchemaValidator> 類別，根據 `contosoBooks.xml` 結構描述驗證 `contosoBooks.xsd` 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="864cc-107">此範例使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將 `contosoBooks.xml` 檔案還原序列化，並將節點的值傳遞給 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864cc-108">此範例用於本主題的各節中。</span><span class="sxs-lookup"><span data-stu-id="864cc-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="864cc-109">該範例採用 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="864cc-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="864cc-110">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="864cc-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="864cc-111">使用 XmlSchemaValidator 驗證 XML 資料</span><span class="sxs-lookup"><span data-stu-id="864cc-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="864cc-112">若要開始驗證 XML 資訊集，您必須先使用 <xref:System.Xml.Schema.XmlSchemaValidator> 建構函式初始化 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="864cc-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="864cc-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式以 <xref:System.Xml.XmlNameTable>、<xref:System.Xml.Schema.XmlSchemaSet> 及 <xref:System.Xml.XmlNamespaceManager>物件做為參數，並以 <xref:System.Xml.Schema.XmlSchemaValidationFlags> 值做為參數。</span><span class="sxs-lookup"><span data-stu-id="864cc-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="864cc-114"><xref:System.Xml.XmlNameTable> 物件可用於儘量縮減已知命名空間字串 (如結構描述命名空間、XML 命名空間等)，並在驗證簡單內容期間，將其傳遞給 <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="864cc-115"><xref:System.Xml.Schema.XmlSchemaSet> 物件包含用於驗證 XML 資訊集的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="864cc-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="864cc-116"><xref:System.Xml.XmlNamespaceManager> 物件可用於解析驗證期間遇到的命名空間。</span><span class="sxs-lookup"><span data-stu-id="864cc-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="864cc-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> 可用於停用某些驗證功能。</span><span class="sxs-lookup"><span data-stu-id="864cc-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="864cc-118">如需 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="864cc-119">初始化驗證</span><span class="sxs-lookup"><span data-stu-id="864cc-119">Initializing Validation</span></span>  
 <span data-ttu-id="864cc-120">建構 <xref:System.Xml.Schema.XmlSchemaValidator> 物件之後，可以採用兩種多載 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="864cc-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="864cc-121">以下是這兩個 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="864cc-122">預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為其開始狀態，以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 做為參數的多載 <xref:System.Xml.Schema.XmlSchemaObject> 方法，會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為開始狀態，以進行部分驗證。</span><span class="sxs-lookup"><span data-stu-id="864cc-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="864cc-123">只有在建構 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 物件或呼叫 <xref:System.Xml.Schema.XmlSchemaValidator> 之後，才可立即呼叫這兩種 <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="864cc-124">如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法的範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="864cc-125">如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="864cc-126">部分驗證</span><span class="sxs-lookup"><span data-stu-id="864cc-126">Partial Validation</span></span>  
 <span data-ttu-id="864cc-127">以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 做為參數的 <xref:System.Xml.Schema.XmlSchemaObject> 方法會將 <xref:System.Xml.Schema.XmlSchemaValidator> 物件初始化為開始狀態，以進行部分驗證。</span><span class="sxs-lookup"><span data-stu-id="864cc-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="864cc-128">在下列範例中，會使用 <xref:System.Xml.Schema.XmlSchemaObject> 方法初始化用於部分驗證的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="864cc-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="864cc-129">傳遞 `orderNumber` 結構描述項目的方法是，在 <xref:System.Xml.XmlQualifiedName> 物件之 <xref:System.Xml.Schema.XmlSchemaObjectTable> 屬性所傳回的 <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> 集合中，依 <xref:System.Xml.Schema.XmlSchemaSet> 選取結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="864cc-130">然後，<xref:System.Xml.Schema.XmlSchemaValidator> 物件會驗證此特定項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
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
  
 <span data-ttu-id="864cc-131">該範例使用下列 XML 結構描述做為輸入。</span><span class="sxs-lookup"><span data-stu-id="864cc-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="864cc-132">如需 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="864cc-133">加入其他結構描述</span><span class="sxs-lookup"><span data-stu-id="864cc-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="864cc-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別的 <xref:System.Xml.Schema.XmlSchemaValidator> 方法，可用於在驗證期間將 XML 結構描述加入至一組結構描述。</span><span class="sxs-lookup"><span data-stu-id="864cc-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="864cc-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法可用於模擬在要驗證之 XML 資訊集中遇到內嵌 XML 結構描述時的效果。</span><span class="sxs-lookup"><span data-stu-id="864cc-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864cc-136"><xref:System.Xml.Schema.XmlSchema> 參數的目標命名空間與 <xref:System.Xml.Schema.XmlSchemaValidator> 物件已遇到之任何項目或屬性的目標命名空間均不相符。</span><span class="sxs-lookup"><span data-stu-id="864cc-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="864cc-137">如果未將 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> 值做為參數傳遞給 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 建構函式，則 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法將不起作用。</span><span class="sxs-lookup"><span data-stu-id="864cc-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="864cc-138"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的結果取決於要驗證的目前 XML 節點內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="864cc-139">如需驗證內容的詳細資訊，請參閱本主題的＜驗證內容＞一節。</span><span class="sxs-lookup"><span data-stu-id="864cc-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="864cc-140">如需 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="864cc-141">驗證項目、屬性及內容</span><span class="sxs-lookup"><span data-stu-id="864cc-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="864cc-142"><xref:System.Xml.Schema.XmlSchemaValidator> 類別提供幾種方法，可用於根據 XML 結構描述驗證 XML 資訊集中的項目、屬性及內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="864cc-143">下表對每個方法進行說明。</span><span class="sxs-lookup"><span data-stu-id="864cc-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="864cc-144">方法</span><span class="sxs-lookup"><span data-stu-id="864cc-144">Method</span></span>|<span data-ttu-id="864cc-145">描述</span><span class="sxs-lookup"><span data-stu-id="864cc-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="864cc-146">驗證目前內容中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="864cc-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="864cc-147">驗證目前項目內容中的屬性，或根據做為參數傳遞給 <xref:System.Xml.Schema.XmlSchemaAttribute> 方法的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 物件驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="864cc-148">驗證項目內容中的所有必要屬性是否均已存在，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件以驗證項目的子內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="864cc-149">驗證目前項目內容中是否允許文字，並且累積文件以驗證目前項目是否有簡單內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="864cc-150">驗證目前項目內容中是否允許泛空白字元，並且累積泛空白字元以驗證目前項目是否有簡單內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="864cc-151">對於含簡單內容的項目，根據其資料型別驗證項目的文字內容是否有效；對於含複雜內容的項目，驗證目前項目的內容是否完整。</span><span class="sxs-lookup"><span data-stu-id="864cc-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="864cc-152">略過目前項目內容的驗證，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件，以驗證父項目內容 (Context) 中的內容 (Content)。</span><span class="sxs-lookup"><span data-stu-id="864cc-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="864cc-153">結束驗證，並且若已設定 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> 驗證選項，則檢查整個 XML 文件的識別條件約束。</span><span class="sxs-lookup"><span data-stu-id="864cc-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="864cc-154"><xref:System.Xml.Schema.XmlSchemaValidator> 類別具有定義的狀態轉換，可強制轉換對前一表格中說明之每個方法的呼叫順序及次數。</span><span class="sxs-lookup"><span data-stu-id="864cc-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="864cc-155"><xref:System.Xml.Schema.XmlSchemaValidator> 類別的特定狀態轉換，在本主題的＜XmlSchemaValidator 狀態轉換＞一節中加以說明。</span><span class="sxs-lookup"><span data-stu-id="864cc-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="864cc-156">如需用來驗證 XML 資訊集中項目、屬性及內容之方法的範例，請參閱前一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="864cc-157">如需這些方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="864cc-158">使用 XmlValueGetter 驗證內容</span><span class="sxs-lookup"><span data-stu-id="864cc-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="864cc-159"><xref:System.Xml.Schema.XmlValueGetter>`delegate` 可用於傳遞屬性、文字或泛空白字元節點的值，成為 Common Language Runtime (CLR) 型別，該型別與它們的 XML 結構描述定義語言 (XSD) 型別相容。</span><span class="sxs-lookup"><span data-stu-id="864cc-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="864cc-160">如果屬性、文字或泛空白字元節點的 CLR 值已經可用，則 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 就很有用，且避免將它轉換為 `string`，然後重新剖析以進行驗證的成本。</span><span class="sxs-lookup"><span data-stu-id="864cc-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="864cc-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> 方法是多載方法，並可接受屬性、文字及泛空白字元節點的值做為 `string` 或 <xref:System.Xml.Schema.XmlValueGetter>`delegate`。</span><span class="sxs-lookup"><span data-stu-id="864cc-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="864cc-162"><xref:System.Xml.Schema.XmlSchemaValidator> 類別的下列方法接受 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 做為參數。</span><span class="sxs-lookup"><span data-stu-id="864cc-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="864cc-163">以下 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 範例取自簡介中的 <xref:System.Xml.Schema.XmlSchemaValidator> 類別範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="864cc-164"><xref:System.Xml.Schema.XmlValueGetter>`delegate` 會將屬性的值做為 <xref:System.DateTime> 物件傳回。</span><span class="sxs-lookup"><span data-stu-id="864cc-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="864cc-165">為驗證 <xref:System.DateTime> 傳回的 <xref:System.Xml.Schema.XmlValueGetter> 物件，<xref:System.Xml.Schema.XmlSchemaValidator> 物件先將其轉換成屬性資料型別 ValueType (ValueType 是 XSD 型別的預設 CLR 對應)，然後檢查已轉換值的 Facet。</span><span class="sxs-lookup"><span data-stu-id="864cc-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 <span data-ttu-id="864cc-166">如需 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 的完整範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="864cc-167">如需 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlValueGetter> 及 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="864cc-168">Post-Schema-Validation-Information</span><span class="sxs-lookup"><span data-stu-id="864cc-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="864cc-169"><xref:System.Xml.Schema.XmlSchemaInfo> 類別表示 <xref:System.Xml.Schema.XmlSchemaValidator> 類別所驗證之 XML 節點的部分後結構描述驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="864cc-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="864cc-170"><xref:System.Xml.Schema.XmlSchemaValidator> 類別的各種方法均可以接受 <xref:System.Xml.Schema.XmlSchemaInfo> 物件做為選擇性 (`null`) `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="864cc-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="864cc-171">成功驗證後，會以驗證的結果設定 <xref:System.Xml.Schema.XmlSchemaInfo> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="864cc-172">例如，使用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法成功驗證屬性後，會以驗證的結果設定 <xref:System.Xml.Schema.XmlSchemaInfo> 物件的 (如果已指定) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> 及 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="864cc-173">下列 <xref:System.Xml.Schema.XmlSchemaValidator> 類別方法接受 <xref:System.Xml.Schema.XmlSchemaInfo> 物件做為輸出參數。</span><span class="sxs-lookup"><span data-stu-id="864cc-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="864cc-174">如需 <xref:System.Xml.Schema.XmlSchemaInfo> 類別的完整範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="864cc-175">如需 <xref:System.Xml.Schema.XmlSchemaInfo> 類別的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaInfo> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="864cc-176">擷取預期物件、屬性及未指定的預設屬性</span><span class="sxs-lookup"><span data-stu-id="864cc-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="864cc-177"><xref:System.Xml.Schema.XmlSchemaValidator> 類別提供 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，以擷取目前驗證內容中的預期物件、屬性及未指定的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="864cc-178">擷取預期物件</span><span class="sxs-lookup"><span data-stu-id="864cc-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="864cc-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回含目前項目內容中預期物件 (Particle) 的 <xref:System.Xml.Schema.XmlSchemaParticle> 物件 (Object) 陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="864cc-180">可由 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法傳回的有效物件為 <xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaAny> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="864cc-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="864cc-181">當內容模型的複合器為 `xs:sequence` 時，只傳回序列中的下一個物件。</span><span class="sxs-lookup"><span data-stu-id="864cc-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="864cc-182">如果內容模型的複合器為 `xs:all` 或 `xs:choice`，則傳回目前項目內容中所有後續的有效物件。</span><span class="sxs-lookup"><span data-stu-id="864cc-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864cc-183">如果在呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法後立即呼叫<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回所有的全域項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="864cc-184">例如，在隨後的 XML 結構描述定義語言 (XSD) 結構描述及 XML 文件中，驗證 `book` 項目之後，`book` 項目會成為目前的項目內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="864cc-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaElement> 物件的陣列，該物件表示 `title` 項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="864cc-186">當驗證內容為 `title` 項目時，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="864cc-187">如果在驗證 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 項目之後、驗證 `title` 項目之前，呼叫 `description` 方法，則它會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaElement> 物件的陣列，該物件表示 `description` 項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="864cc-188">如果在驗證 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 項目之後呼叫 `description` 方法，則它會傳回包含單一 <xref:System.Xml.Schema.XmlSchemaAny> 物件的陣列，該物件表示萬用字元。</span><span class="sxs-lookup"><span data-stu-id="864cc-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
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
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
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
  
 <span data-ttu-id="864cc-189">該範例使用下列 XML 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="864cc-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="864cc-190">該範例使用下列 XSD 結構描述做為輸入。</span><span class="sxs-lookup"><span data-stu-id="864cc-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="864cc-191"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="864cc-192">如需詳細資訊，請參閱本主題的＜驗證內容＞一節。</span><span class="sxs-lookup"><span data-stu-id="864cc-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="864cc-193">如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="864cc-194">如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="864cc-195">擷取預期屬性</span><span class="sxs-lookup"><span data-stu-id="864cc-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="864cc-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法會傳回含目前項目內容中預期屬性的 <xref:System.Xml.Schema.XmlSchemaAttribute> 物件陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="864cc-197">例如，在簡介內的範例中，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法用於擷取 `book` 項目的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="864cc-198">如果在呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法之後立即呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> 方法，則會傳回 XML 文件中出現的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="864cc-199">但是，如果在對 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法進行一或多次呼叫之後呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法，則會傳回目前項目之尚未驗證的屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864cc-200"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="864cc-201">如需詳細資訊，請參閱本主題的＜驗證內容＞一節。</span><span class="sxs-lookup"><span data-stu-id="864cc-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="864cc-202">如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="864cc-203">如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="864cc-204">擷取未指定的預設屬性</span><span class="sxs-lookup"><span data-stu-id="864cc-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="864cc-205">對於項目內容中其預設值尚未使用 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法加以驗證的任何屬性，<xref:System.Collections.ArrayList> 方法以 <xref:System.Xml.Schema.XmlSchemaAttribute> 物件填入指定的 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="864cc-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="864cc-206">應先在項目內容中的每個屬性上呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，再呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="864cc-207">應使用 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法，判斷要將哪些預設屬性插入要驗證的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="864cc-208">如需 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaValidator> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="864cc-209">處理結構描述驗證事件</span><span class="sxs-lookup"><span data-stu-id="864cc-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="864cc-210"><xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> 類別的 <xref:System.Xml.Schema.XmlSchemaValidator> 事件會處理驗證期間發生的結構描述驗證警告及錯誤。</span><span class="sxs-lookup"><span data-stu-id="864cc-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="864cc-211">結構描述驗證警告的 <xref:System.Xml.Schema.XmlSeverityType> 值為 <xref:System.Xml.Schema.XmlSeverityType.Warning>；結構描述驗證錯誤的 <xref:System.Xml.Schema.XmlSeverityType> 值為 <xref:System.Xml.Schema.XmlSeverityType.Error>。</span><span class="sxs-lookup"><span data-stu-id="864cc-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="864cc-212">如果尚未指派 <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>，則會針對 <xref:System.Xml.Schema.XmlSchemaValidationException> 值為 <xref:System.Xml.Schema.XmlSeverityType> 的所有結構描述驗證錯誤，擲回 <xref:System.Xml.Schema.XmlSeverityType.Error>。</span><span class="sxs-lookup"><span data-stu-id="864cc-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="864cc-213">但是，對於 <xref:System.Xml.Schema.XmlSchemaValidationException> 值為 <xref:System.Xml.Schema.XmlSeverityType> 的結構描述驗證警告，則不會擲回 <xref:System.Xml.Schema.XmlSeverityType.Warning>。</span><span class="sxs-lookup"><span data-stu-id="864cc-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="864cc-214">以下內容取自簡介中，擷取結構描述驗證期間發生之結構描述驗證警告及錯誤的 <xref:System.Xml.Schema.ValidationEventHandler> 範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
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
  
 <span data-ttu-id="864cc-215">如需 <xref:System.Xml.Schema.ValidationEventHandler> 的完整範例，請參閱簡介中的範例。</span><span class="sxs-lookup"><span data-stu-id="864cc-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="864cc-216">如需詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaInfo> 類別參考文件。</span><span class="sxs-lookup"><span data-stu-id="864cc-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="864cc-217">XmlSchemaValidator 狀態轉換</span><span class="sxs-lookup"><span data-stu-id="864cc-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="864cc-218"><xref:System.Xml.Schema.XmlSchemaValidator> 類別具有定義的狀態轉換，可強制轉換用於驗證 XML 資訊集內項目、屬性及內容之每個方法的呼叫順序及次數。</span><span class="sxs-lookup"><span data-stu-id="864cc-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="864cc-219">下表說明 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的狀態轉換，以及在每個狀態下可進行之方法呼叫的順序及次數。</span><span class="sxs-lookup"><span data-stu-id="864cc-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="864cc-220">狀況</span><span class="sxs-lookup"><span data-stu-id="864cc-220">State</span></span>|<span data-ttu-id="864cc-221">轉換</span><span class="sxs-lookup"><span data-stu-id="864cc-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="864cc-222">Validate</span><span class="sxs-lookup"><span data-stu-id="864cc-222">Validate</span></span>|<span data-ttu-id="864cc-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="864cc-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="864cc-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="864cc-224">TopLevel</span></span>|<span data-ttu-id="864cc-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; 項目</span><span class="sxs-lookup"><span data-stu-id="864cc-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="864cc-226">元素</span><span class="sxs-lookup"><span data-stu-id="864cc-226">Element</span></span>|<span data-ttu-id="864cc-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span><span class="sxs-lookup"><span data-stu-id="864cc-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="864cc-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="864cc-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="864cc-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="864cc-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="864cc-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="864cc-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="864cc-231">內容</span><span class="sxs-lookup"><span data-stu-id="864cc-231">Content</span></span>|<span data-ttu-id="864cc-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; 項目</span><span class="sxs-lookup"><span data-stu-id="864cc-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="864cc-233">根據 <xref:System.InvalidOperationException> 物件的目前狀態，如果呼叫上表中的每個方法的順序不正確，則它們會擲回 <xref:System.Xml.Schema.XmlSchemaValidator>。</span><span class="sxs-lookup"><span data-stu-id="864cc-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="864cc-234">以上狀態轉換表會使用標點符號，說明可針對 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之狀態轉換的每個狀態呼叫的方法及其他狀態。</span><span class="sxs-lookup"><span data-stu-id="864cc-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="864cc-235">所使用的符號與在物件型別定義 (DTD) 之 XML 標準參考中找到的符號相同。</span><span class="sxs-lookup"><span data-stu-id="864cc-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="864cc-236">下表說明在以上狀態轉換表中找到的標點符號，如何影響針對 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之狀態轉換中每個狀態呼叫的方法及其他狀態。</span><span class="sxs-lookup"><span data-stu-id="864cc-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="864cc-237">符號</span><span class="sxs-lookup"><span data-stu-id="864cc-237">Symbol</span></span>|<span data-ttu-id="864cc-238">描述</span><span class="sxs-lookup"><span data-stu-id="864cc-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="864cc-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="864cc-239">&#124;</span></span>|<span data-ttu-id="864cc-240">可呼叫方法或狀態 (垂直線前後的項目)。</span><span class="sxs-lookup"><span data-stu-id="864cc-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="864cc-241">?</span><span class="sxs-lookup"><span data-stu-id="864cc-241">?</span></span>|<span data-ttu-id="864cc-242">問號之前的方法或狀態是選擇性的，但如果呼叫它，則只能呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="864cc-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="864cc-243">\* 符號之前的方法或狀態是選擇性的，可對其呼叫多次。</span><span class="sxs-lookup"><span data-stu-id="864cc-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="864cc-244">驗證內容</span><span class="sxs-lookup"><span data-stu-id="864cc-244">Validation Context</span></span>  
 <span data-ttu-id="864cc-245">用於驗證 XML 資訊集中項目、屬性及內容之 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的方法，可變更 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的驗證內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="864cc-246">例如，<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> 方法會略過目前項目內容的驗證，並準備 <xref:System.Xml.Schema.XmlSchemaValidator> 物件以驗證父項目內容 (Context) 中的內容 (Content)；這相當於略過目前項目之所有項目子系的驗證，並呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="864cc-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="864cc-247"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 及 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 類別之 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的結果，取決於要驗證的目前內容。</span><span class="sxs-lookup"><span data-stu-id="864cc-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="864cc-248">下表說明在呼叫用於驗證 XML 資訊集中項目、屬性及內容之 <xref:System.Xml.Schema.XmlSchemaValidator> 類別的其中一個方法之後，呼叫這些方法的結果。</span><span class="sxs-lookup"><span data-stu-id="864cc-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="864cc-249">方法</span><span class="sxs-lookup"><span data-stu-id="864cc-249">Method</span></span>|<span data-ttu-id="864cc-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="864cc-250">GetExpectedParticles</span></span>|<span data-ttu-id="864cc-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="864cc-251">GetExpectedAttributes</span></span>|<span data-ttu-id="864cc-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="864cc-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="864cc-253">如果呼叫預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回包含所有全域項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="864cc-254">如果呼叫以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 做為參數之多載 <xref:System.Xml.Schema.XmlSchemaObject> 方法，以初始化項目的部分驗證，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 僅會傳回已初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的項目。</span><span class="sxs-lookup"><span data-stu-id="864cc-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="864cc-255">如果呼叫預設的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-256">如果呼叫以 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 做為參數之 <xref:System.Xml.Schema.XmlSchemaObject> 方法的多載，以初始化屬性的部分驗證，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 僅會傳回已初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="864cc-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="864cc-257">如果結構描述未發生前置處理錯誤，則將其加入 <xref:System.Xml.Schema.XmlSchemaSet> 物件的<xref:System.Xml.Schema.XmlSchemaValidator>。</span><span class="sxs-lookup"><span data-stu-id="864cc-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="864cc-258">如果內容項目有效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之項目子系的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="864cc-259">如果內容項目無效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="864cc-260">如果內容項目有效，且先前並未呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>，則<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回內容項目上定義之所有屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="864cc-261">如果已驗證部分屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之其餘屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="864cc-262">如果內容項目無效，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="864cc-263">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="864cc-264">如果內容屬性是最上層屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-265">否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="864cc-266">如果內容屬性是最上層屬性，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-267">否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之其餘屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="864cc-268">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="864cc-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="864cc-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回要驗證之內容項目的必要及選擇性屬性清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="864cc-271">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="864cc-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期為內容項目之第一個項目子系的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="864cc-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="864cc-274">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="864cc-275">如果內容項目的 contentType 為 Mixed，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回下一個位置中預期的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="864cc-276">如果內容項目的 contentType 為 TextOnly 或 Empty，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-277">如果內容項目的 contentType 為 ElementOnly，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回下一個位置中預期的、但已發生驗證錯誤的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="864cc-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回未驗證之屬性的內容項目清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="864cc-279">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="864cc-280">如果內容泛空白字元是最上層泛空白字元，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-281">否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的行為與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中的相同。</span><span class="sxs-lookup"><span data-stu-id="864cc-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="864cc-282">如果內容泛空白字元是最上層泛空白字元，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="864cc-283">否則，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的行為與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中的相同。</span><span class="sxs-lookup"><span data-stu-id="864cc-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="864cc-284">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="864cc-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 會傳回預期位於內容項目之後 (可能為同層級) 的項目序列。</span><span class="sxs-lookup"><span data-stu-id="864cc-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="864cc-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回未驗證之屬性的內容項目清單。</span><span class="sxs-lookup"><span data-stu-id="864cc-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="864cc-287">如果內容項目沒有父代，則 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 會傳回空清單 (內容項目是已呼叫 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 之目前項目的父代)。</span><span class="sxs-lookup"><span data-stu-id="864cc-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="864cc-288">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="864cc-289">與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。</span><span class="sxs-lookup"><span data-stu-id="864cc-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="864cc-290">與 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。</span><span class="sxs-lookup"><span data-stu-id="864cc-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="864cc-291">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="864cc-292">傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-292">Returns an empty array.</span></span>|<span data-ttu-id="864cc-293">傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="864cc-293">Returns an empty array.</span></span>|<span data-ttu-id="864cc-294">同上。</span><span class="sxs-lookup"><span data-stu-id="864cc-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="864cc-295">呼叫上表中的任何方法，均不會改變 <xref:System.Xml.Schema.XmlSchemaValidator> 類別之各種屬性所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="864cc-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864cc-296">請參閱</span><span class="sxs-lookup"><span data-stu-id="864cc-296">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaValidator>
