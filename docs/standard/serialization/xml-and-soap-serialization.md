---
title: XML 和 SOAP 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028235"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="43460-102">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="43460-102">XML and SOAP Serialization</span></span>

<span data-ttu-id="43460-103">XML 序列化會將物件的公用 (Public) 欄位和屬性，或是方法的參數和傳回值，轉換 (序列化) 為與特定 XML 結構描述 (Schema) 定義語言 (XSD) 文件相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="43460-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="43460-104">XML 序列化會產生強型別 (Strongly Typed) 類別，其中包含的公用屬性和欄位都轉換為序列格式 (此例為 XML) 以進行儲存或傳輸。</span><span class="sxs-lookup"><span data-stu-id="43460-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="43460-105">因為 XML 為開放標準，無論是何種平台，XML 資料流都可依需要由任何應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="43460-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="43460-106">例如，使用 ASP.NET 建立的 XML Web 服務以 <xref:System.Xml.Serialization.XmlSerializer> 類別建立 XML 資料流，在網際網路或內部網路的 XML Web 服務應用程式之間傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="43460-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="43460-107">相反地，還原序列化採用這樣的 XML 資料流並重建物件。</span><span class="sxs-lookup"><span data-stu-id="43460-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="43460-108">XML 序列化也可用來將物件序列化為與 SOAP 規格相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="43460-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="43460-109">SOAP 是以 XML 為基礎的通訊協定，特別設計來傳輸使用 XML 的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="43460-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="43460-110">若要序列化或還原序列化物件，請使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="43460-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="43460-111">若要建立要序列化的類別，請使用 XML 結構描述定義工具。</span><span class="sxs-lookup"><span data-stu-id="43460-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="43460-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="43460-112">In This Section</span></span>

[<span data-ttu-id="43460-113">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="43460-113">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
<span data-ttu-id="43460-114">提供序列化的一般定義，特別是 XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="43460-114">Provides a general definition of serialization, particularly XML serialization.</span></span>

[<span data-ttu-id="43460-115">如何：將物件序列化</span><span class="sxs-lookup"><span data-stu-id="43460-115">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
<span data-ttu-id="43460-116">提供序列化物件的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="43460-116">Provides step-by-step instructions for serializing an object.</span></span>

[<span data-ttu-id="43460-117">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="43460-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  
<span data-ttu-id="43460-118">提供還原序列化物件的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="43460-118">Provides step-by-step instructions for deserializing an object.</span></span>

[<span data-ttu-id="43460-119">XML 序列化範例</span><span class="sxs-lookup"><span data-stu-id="43460-119">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
<span data-ttu-id="43460-120">提供範例示範 XML 序列化的基本概念。</span><span class="sxs-lookup"><span data-stu-id="43460-120">Provides examples that demonstrate the basics of XML serialization.</span></span>

[<span data-ttu-id="43460-121">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="43460-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)  
<span data-ttu-id="43460-122">說明如何使用 XML 結構描述定義工具，建立遵循特定 XML 結構描述定義語言 (XSD) 結構描述的類別，或是從 .dll 檔案產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="43460-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>

[<span data-ttu-id="43460-123">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="43460-123">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)  
<span data-ttu-id="43460-124">說明如何使用屬性控制序列化。</span><span class="sxs-lookup"><span data-stu-id="43460-124">Describes how to control serialization by using attributes.</span></span>

[<span data-ttu-id="43460-125">可控制 XML 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="43460-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
<span data-ttu-id="43460-126">列出用來控制 XML 序列化的屬性。</span><span class="sxs-lookup"><span data-stu-id="43460-126">Lists the attributes that are used to control XML serialization.</span></span>

[<span data-ttu-id="43460-127">如何：指定 XML Stream 的替代項目名稱</span><span class="sxs-lookup"><span data-stu-id="43460-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
<span data-ttu-id="43460-128">提供進階案例展示如何藉由覆寫序列化產生多個 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="43460-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>

[<span data-ttu-id="43460-129">如何：控制序列化的衍生類別的</span><span class="sxs-lookup"><span data-stu-id="43460-129">How to: Control Serialization of Derived Classes</span></span>](how-to-control-serialization-of-derived-classes.md)  
<span data-ttu-id="43460-130">提供如何控制衍生類別序列化的範例。</span><span class="sxs-lookup"><span data-stu-id="43460-130">Provides an example of how to control the serialization of derived classes.</span></span>

[<span data-ttu-id="43460-131">如何：限定 XML 元素和 XML 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="43460-131">How to: Qualify XML Element and XML Attribute Names</span></span>](how-to-qualify-xml-element-and-xml-attribute-names.md)  
<span data-ttu-id="43460-132">說明如何定義並控制 XML 命名空間在 XML 資料流中使用的方式。</span><span class="sxs-lookup"><span data-stu-id="43460-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>

[<span data-ttu-id="43460-133">以 XML Web 服務進行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="43460-133">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)  
<span data-ttu-id="43460-134">說明 XML 序列化如何用於 XML Web 服務當中。</span><span class="sxs-lookup"><span data-stu-id="43460-134">Explains how XML serialization is used in XML Web services.</span></span>

[<span data-ttu-id="43460-135">如何：將物件序列化為 SOAP 編碼的 XML Stream</span><span class="sxs-lookup"><span data-stu-id="43460-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
<span data-ttu-id="43460-136">描述如何使用<xref:System.Xml.Serialization.XmlSerializer>類別來建立符合第 5 節的 World Wide Web Consortium (W3C) 文件的編碼的 SOAP XML 資料流[簡易物件存取通訊協定 (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)。</span><span class="sxs-lookup"><span data-stu-id="43460-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span></span>

[<span data-ttu-id="43460-137">如何：覆寫編碼的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="43460-137">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
<span data-ttu-id="43460-138">說明將物件的 XML 序列化覆寫為 SOAP 訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="43460-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>

[<span data-ttu-id="43460-139">可控制編碼 SOAP 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="43460-139">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
<span data-ttu-id="43460-140">列出用來控制 SOAP 編碼序列化的屬性。</span><span class="sxs-lookup"><span data-stu-id="43460-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>

[<span data-ttu-id="43460-141">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="43460-141">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)  
<span data-ttu-id="43460-142">用來控制 XML 序列化的最上層組態項目。</span><span class="sxs-lookup"><span data-stu-id="43460-142">The top-level configuration element for controlling XML serialization.</span></span>

[<span data-ttu-id="43460-143">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="43460-143">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)  
<span data-ttu-id="43460-144">控制 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="43460-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>

[<span data-ttu-id="43460-145">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="43460-145">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)  
<span data-ttu-id="43460-146">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。</span><span class="sxs-lookup"><span data-stu-id="43460-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

[<span data-ttu-id="43460-147">\<新增 > 項目\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="43460-147">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)  
<span data-ttu-id="43460-148">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。</span><span class="sxs-lookup"><span data-stu-id="43460-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

## <a name="related-sections"></a><span data-ttu-id="43460-149">相關章節</span><span class="sxs-lookup"><span data-stu-id="43460-149">Related Sections</span></span>

<span data-ttu-id="43460-150">[使用 ASP.NET 和 XML Web Service 用戶端建立的 XML Web Service](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43460-150">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>  
<span data-ttu-id="43460-151">提供一個主題，說明並解釋如何設計使用 ASP.NET 的 XML Web 服務。</span><span class="sxs-lookup"><span data-stu-id="43460-151">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="43460-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43460-152">See also</span></span>

- [<span data-ttu-id="43460-153">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="43460-153">Binary Serialization</span></span>](binary-serialization.md)
