---
title: 驗證 DOM 中的 XML 文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b25bf81a17b14da558fb002b4740e31d6cda7a82
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040457"
---
# <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="433aa-102">驗證 DOM 中的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="433aa-102">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="433aa-103">依預設，<xref:System.Xml.XmlDocument> 類別不會根據 XML 結構描述定義語言 (XSD) 結構描述或文件類型定義 (DTD) 來驗證文件物件模型 (DOM) 中的 XML；其只會驗證 XML 的格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="433aa-103">The<xref:System.Xml.XmlDocument> class does not validate the XML in the Document Object Model (DOM) against an XML Schema definition language (XSD) schema or document type definition (DTD) by default; the XML is only verified to be well-formed.</span></span>

<span data-ttu-id="433aa-104">若要驗證 DOM 中的 XML，您可以在將 XML 載入到 DOM 時，藉由將結構描述驗證的 <xref:System.Xml.XmlReader> 傳遞至 <xref:System.Xml.XmlDocument.Load%2A> 類別的 <xref:System.Xml.XmlDocument> 方法來驗證它，也可使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，驗證 DOM 中先前未驗證的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="433aa-104">To validate the XML in the DOM, you can validate the XML as it is loaded into the DOM by passing a schema-validating <xref:System.Xml.XmlReader> to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class, or validate a previously unvalidated XML document in the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a><span data-ttu-id="433aa-105">將 XML 文件載入到 DOM 時進行驗證</span><span class="sxs-lookup"><span data-stu-id="433aa-105">Validating an XML Document As It Is Loaded into the DOM</span></span>

<span data-ttu-id="433aa-106">在將驗證 <xref:System.Xml.XmlDocument> 傳遞至 <xref:System.Xml.XmlReader> 類別的 <xref:System.Xml.XmlDocument.Load%2A> 方法時，<xref:System.Xml.XmlDocument> 類別會在 XML 資料載入 DOM 時加以驗證。</span><span class="sxs-lookup"><span data-stu-id="433aa-106">The <xref:System.Xml.XmlDocument> class validates the XML data as it is loaded into the DOM when a validating <xref:System.Xml.XmlReader> is passed to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

<span data-ttu-id="433aa-107">在驗證成功之後，會套用結構描述預設值，視需要將文字值轉換成原子值，並將類型資訊與已驗證的資訊項目相關聯。</span><span class="sxs-lookup"><span data-stu-id="433aa-107">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="433aa-108">因此，具類型的 XML 資料會取代先前不具類型的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="433aa-108">As a result, typed XML data replaces previously untyped XML data.</span></span>

### <a name="creating-an-xml-schema-validating-xmlreader"></a><span data-ttu-id="433aa-109">建立 XML 結構描述驗證的 XmlReader</span><span class="sxs-lookup"><span data-stu-id="433aa-109">Creating an XML Schema-Validating XmlReader</span></span>

<span data-ttu-id="433aa-110">若要建立 XML 結構描述驗證的 <xref:System.Xml.XmlReader>，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="433aa-110">To create an XML schema-validating <xref:System.Xml.XmlReader>, follow these steps.</span></span>

1. <span data-ttu-id="433aa-111">建構新的 <xref:System.Xml.XmlReaderSettings> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="433aa-111">Construct a new <xref:System.Xml.XmlReaderSettings> instance.</span></span>

2. <span data-ttu-id="433aa-112">將 XML 結構描述加入至 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 執行個體的 <xref:System.Xml.XmlReaderSettings> 屬性。</span><span class="sxs-lookup"><span data-stu-id="433aa-112">Add an XML schema to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> instance.</span></span>

3. <span data-ttu-id="433aa-113">指定 `Schema` 做為 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>。</span><span class="sxs-lookup"><span data-stu-id="433aa-113">Specify `Schema` as the <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.</span></span>

4. <span data-ttu-id="433aa-114">選擇性地指定 <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> 及 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>，以處理驗證期間遇到的結構描述驗證錯誤及警告。</span><span class="sxs-lookup"><span data-stu-id="433aa-114">Optionally specify <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> and a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> to handle schema validation errors and warnings encountered during validation.</span></span>

5. <span data-ttu-id="433aa-115">最後，將 <xref:System.Xml.XmlReaderSettings> 物件傳遞至 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法，及傳遞至 XML 文件，建立結構描述驗證的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="433aa-115">Finally, pass the <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class along with the XML document, creating a schema-validating <xref:System.Xml.XmlReader>.</span></span>

### <a name="example"></a><span data-ttu-id="433aa-116">範例</span><span class="sxs-lookup"><span data-stu-id="433aa-116">Example</span></span>

<span data-ttu-id="433aa-117">在下面的程式碼範例中，結構描述驗證的 <xref:System.Xml.XmlReader> 會驗證載入至 DOM 的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="433aa-117">In the code example that follows, a schema-validating <xref:System.Xml.XmlReader> validates the XML data loaded into the DOM.</span></span> <span data-ttu-id="433aa-118">對 XML 文件進行無效的修改，然後重新驗證該文件，會導致結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="433aa-118">Invalid modifications are made to the XML document and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="433aa-119">最後，更正其中一個錯誤，然後對 XML 文件的一部分進行部分驗證。</span><span class="sxs-lookup"><span data-stu-id="433aa-119">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="433aa-120">該範例採用 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="433aa-120">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="433aa-121">該範例還將 `contosoBooks.xsd` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="433aa-121">The example also takes the `contosoBooks.xsd` file as input.</span></span>

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

<span data-ttu-id="433aa-122">在驗證載入至 DOM 的 XML 資料時，請考量下列事項。</span><span class="sxs-lookup"><span data-stu-id="433aa-122">Consider the following when validating XML data as it is loaded into the DOM.</span></span>

- <span data-ttu-id="433aa-123">在上述範例中，每當遇到無效的類型時，就會呼叫 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="433aa-123">In the above example, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is called whenever an invalid type is encountered.</span></span> <span data-ttu-id="433aa-124">如果 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 未在要進行驗證的 <xref:System.Xml.XmlReader> 中設定，若因任何屬性或項目與要進行驗證之結構描述中指定的對應類型不符合，而呼叫 <xref:System.Xml.Schema.XmlSchemaValidationException> 時，則會擲回 <xref:System.Xml.XmlDocument.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="433aa-124">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is not set on the validating <xref:System.Xml.XmlReader>,an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span>

- <span data-ttu-id="433aa-125">當 XML 文件載入至具有可定義預設值之關聯結構描述的 <xref:System.Xml.XmlDocument> 物件時，<xref:System.Xml.XmlDocument> 會處理這些預設值，就好像它們是出現在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="433aa-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="433aa-126">這表示 <xref:System.Xml.XmlReader.IsEmptyElement%2A> 屬性針對該結構描述預設會產生的項目，永遠傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="433aa-126">This means that the <xref:System.Xml.XmlReader.IsEmptyElement%2A> property always returns `false` for an element that was defaulted from the schema.</span></span> <span data-ttu-id="433aa-127">即使在 XML 文件中，它也做為空白項目寫入。</span><span class="sxs-lookup"><span data-stu-id="433aa-127">Even if in the XML document, it was written as an empty element.</span></span>

## <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="433aa-128">驗證 DOM 中的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="433aa-128">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="433aa-129">根據 <xref:System.Xml.XmlDocument.Validate%2A> 物件之 <xref:System.Xml.XmlDocument> 屬性中的結構描述，<xref:System.Xml.XmlDocument> 類別的 <xref:System.Xml.XmlDocument.Schemas%2A> 方法會驗證載入到 DOM 的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="433aa-129">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML data loaded in the DOM against the schemas in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span> <span data-ttu-id="433aa-130">在驗證成功之後，會套用結構描述預設值，視需要將文字值轉換成原子值，並將類型資訊與已驗證的資訊項目相關聯。</span><span class="sxs-lookup"><span data-stu-id="433aa-130">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="433aa-131">因此，具類型的 XML 資料會取代先前不具類型的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="433aa-131">As a result, typed XML data replaces previously untyped XML data.</span></span>

<span data-ttu-id="433aa-132">以下範例與上述＜將 XML 文件載入到 DOM 時進行驗證＞中的範例相似。</span><span class="sxs-lookup"><span data-stu-id="433aa-132">The example below is similar to the example in "Validating an XML Document As It Is Loaded into the DOM" above.</span></span> <span data-ttu-id="433aa-133">在此範例中，XML 文件不是在載入到 DOM 時進行驗證，而是在載入到 DOM 之後，使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法進行驗證。</span><span class="sxs-lookup"><span data-stu-id="433aa-133">In this example, the XML document is not validated as it is loaded into the DOM, but rather is validated after it has been loaded into the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="433aa-134"><xref:System.Xml.XmlDocument.Validate%2A> 方法會根據 <xref:System.Xml.XmlDocument.Schemas%2A> 的 <xref:System.Xml.XmlDocument> 屬性中包含的 XML 結構描述，驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="433aa-134">The <xref:System.Xml.XmlDocument.Validate%2A> method validates the XML document against the XML schemas contained in the <xref:System.Xml.XmlDocument.Schemas%2A> property of the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="433aa-135">然後對 XML 文件進行無效的修改並重新驗證該文件，會導致結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="433aa-135">Invalid modifications are then made to the XML document, and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="433aa-136">最後，更正其中一個錯誤，然後對 XML 文件的一部分進行部分驗證。</span><span class="sxs-lookup"><span data-stu-id="433aa-136">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="433aa-137">該範例將上述＜將 XML 文件載入到 DOM 時進行驗證＞所指的 `contosoBooks.xml` 及 `contosoBooks.xsd` 檔案當做輸入。</span><span class="sxs-lookup"><span data-stu-id="433aa-137">The example takes as input the `contosoBooks.xml` and `contosoBooks.xsd` files referred to in "Validating an XML Document as it is Loaded into the DOM" above.</span></span>

## <a name="handling-validation-errors-and-warnings"></a><span data-ttu-id="433aa-138">處理驗證錯誤及警告</span><span class="sxs-lookup"><span data-stu-id="433aa-138">Handling Validation Errors and Warnings</span></span>

<span data-ttu-id="433aa-139">驗證載入 DOM 中的 XML 資料時，會報告 XML 結構描述驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="433aa-139">XML schema validation errors are reported when validating XML data loaded in the DOM.</span></span> <span data-ttu-id="433aa-140">會通知您在驗證載入的 XML 資料時，或者驗證先前未驗證的 XML 文件時，所找到的全部結構描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="433aa-140">You are notified about all schema validation errors found while validating the XML data as it is being loaded, or when validating a previously unvalidated XML document.</span></span>

<span data-ttu-id="433aa-141">驗證錯誤由 <xref:System.Xml.Schema.ValidationEventHandler> 來處理。</span><span class="sxs-lookup"><span data-stu-id="433aa-141">Validation errors are handled by the <xref:System.Xml.Schema.ValidationEventHandler>.</span></span> <span data-ttu-id="433aa-142">如果將 <xref:System.Xml.Schema.ValidationEventHandler> 指派給 <xref:System.Xml.XmlReaderSettings> 執行個體，或傳遞至 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，則 <xref:System.Xml.Schema.ValidationEventHandler> 將處理結構描述驗證錯誤；否則當遇到結構描述驗證錯誤時，會引發 <xref:System.Xml.Schema.XmlSchemaValidationException>。</span><span class="sxs-lookup"><span data-stu-id="433aa-142">If a <xref:System.Xml.Schema.ValidationEventHandler> was assigned to the <xref:System.Xml.XmlReaderSettings> instance, or passed to the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.Schema.ValidationEventHandler> will handle schema validation errors; otherwise an <xref:System.Xml.Schema.XmlSchemaValidationException> is raised when a schema validation error is encountered.</span></span>

> [!NOTE]
> <span data-ttu-id="433aa-143">除非 <xref:System.Xml.Schema.ValidationEventHandler> 引發例外狀況並停止處理序，否則即使發生結構描述驗證錯誤，也會將 XML 資料載入到 DOM。</span><span class="sxs-lookup"><span data-stu-id="433aa-143">The XML data is loaded into the DOM despite schema validation errors unless your <xref:System.Xml.Schema.ValidationEventHandler> raises an exception to stop the process.</span></span>
>
> <span data-ttu-id="433aa-144">除非將 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> 旗標指定至 <xref:System.Xml.XmlReaderSettings> 物件，否則不會報告結構描述驗證警告。</span><span class="sxs-lookup"><span data-stu-id="433aa-144">Schema validation warnings are not reported unless the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> flag is specified to the <xref:System.Xml.XmlReaderSettings> object.</span></span>

 <span data-ttu-id="433aa-145">如需說明 <xref:System.Xml.Schema.ValidationEventHandler> 的範例，請參閱上述＜將 XML 文件載入到 DOM 時進行驗證＞及＜驗證 DOM 中的 XML 文件＞。</span><span class="sxs-lookup"><span data-stu-id="433aa-145">For examples illustrating the <xref:System.Xml.Schema.ValidationEventHandler>, see "Validating an XML Document As It Is Loaded into the DOM" and "Validating an XML Document in the DOM" above.</span></span>

## <a name="see-also"></a><span data-ttu-id="433aa-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="433aa-146">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [<span data-ttu-id="433aa-147">使用 DOM 模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="433aa-147">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [<span data-ttu-id="433aa-148">使用 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="433aa-148">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
