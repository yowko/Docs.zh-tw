---
title: "XML 和 SOAP 序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5b89392801e7cf85fcda121a86d0bda4e7ac18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="5857f-102">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="5857f-103">XML 序列化會將物件的公用 (Public) 欄位和屬性，或是方法的參數和傳回值，轉換 (序列化) 為與特定 XML 結構描述 (Schema) 定義語言 (XSD) 文件相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="5857f-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="5857f-104">XML 序列化會產生強型別 (Strongly Typed) 類別，其中包含的公用屬性和欄位都轉換為序列格式 (此例為 XML) 以進行儲存或傳輸。</span><span class="sxs-lookup"><span data-stu-id="5857f-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="5857f-105">因為 XML 為開放標準，無論是何種平台，XML 資料流都可依需要由任何應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="5857f-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="5857f-106">例如，使用 ASP.NET 建立的 XML Web 服務以 <xref:System.Xml.Serialization.XmlSerializer> 類別建立 XML 資料流，在網際網路或內部網路的 XML Web 服務應用程式之間傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="5857f-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="5857f-107">相反地，還原序列化採用這樣的 XML 資料流並重建物件。</span><span class="sxs-lookup"><span data-stu-id="5857f-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="5857f-108">XML 序列化也可用來將物件序列化為與 SOAP 規格相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="5857f-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="5857f-109">SOAP 是以 XML 為基礎的通訊協定，特別設計來傳輸使用 XML 的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="5857f-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="5857f-110">若要序列化或還原序列化物件，請使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="5857f-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="5857f-111">若要建立要序列化的類別，請使用 XML 結構描述定義工具。</span><span class="sxs-lookup"><span data-stu-id="5857f-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5857f-112">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5857f-112">In This Section</span></span>  
 [<span data-ttu-id="5857f-113">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="5857f-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="5857f-114">提供序列化的一般定義，特別是 XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="5857f-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="5857f-115">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="5857f-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="5857f-116">提供序列化物件的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="5857f-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="5857f-117">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="5857f-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="5857f-118">提供還原序列化物件的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="5857f-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="5857f-119">XML 序列化範例</span><span class="sxs-lookup"><span data-stu-id="5857f-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="5857f-120">提供範例示範 XML 序列化的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5857f-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="5857f-121">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="5857f-122">說明如何使用 XML 結構描述定義工具，建立遵循特定 XML 結構描述定義語言 (XSD) 結構描述的類別，或是從 .dll 檔案產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="5857f-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="5857f-123">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="5857f-124">說明如何使用屬性控制序列化。</span><span class="sxs-lookup"><span data-stu-id="5857f-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="5857f-125">可控制 XML 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="5857f-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="5857f-126">列出用來控制 XML 序列化的屬性。</span><span class="sxs-lookup"><span data-stu-id="5857f-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="5857f-127">如何：指定 XML 資料流的替代元素名稱</span><span class="sxs-lookup"><span data-stu-id="5857f-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="5857f-128">提供進階案例展示如何藉由覆寫序列化產生多個 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="5857f-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="5857f-129">如何：控制衍生類別的序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="5857f-130">提供如何控制衍生類別序列化的範例。</span><span class="sxs-lookup"><span data-stu-id="5857f-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="5857f-131">如何：限定 XML 元素和 XML 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="5857f-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="5857f-132">說明如何定義並控制 XML 命名空間在 XML 資料流中使用的方式。</span><span class="sxs-lookup"><span data-stu-id="5857f-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="5857f-133">以 XML Web 服務進行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="5857f-134">說明 XML 序列化如何用於 XML Web 服務當中。</span><span class="sxs-lookup"><span data-stu-id="5857f-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="5857f-135">如何：將物件序列化為 SOAP 編碼的 XML 資料流</span><span class="sxs-lookup"><span data-stu-id="5857f-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="5857f-136">說明如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別建立編碼 SOAP XML 資料流，這些資料流符合全球資訊網協會 (www.w3.org) 文件＜Simple Object Access Protocol (SOAP) 1.1＞的第 5 節。</span><span class="sxs-lookup"><span data-stu-id="5857f-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="5857f-137">如何：覆寫已編碼的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="5857f-138">說明將物件的 XML 序列化覆寫為 SOAP 訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="5857f-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="5857f-139">可控制編碼 SOAP 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="5857f-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="5857f-140">列出用來控制 SOAP 編碼序列化的屬性。</span><span class="sxs-lookup"><span data-stu-id="5857f-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="5857f-141">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="5857f-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="5857f-142">用來控制 XML 序列化的最上層組態項目。</span><span class="sxs-lookup"><span data-stu-id="5857f-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="5857f-143">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="5857f-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="5857f-144">控制 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="5857f-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="5857f-145">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="5857f-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="5857f-146">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。</span><span class="sxs-lookup"><span data-stu-id="5857f-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="5857f-147">\<xmlSchemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="5857f-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="5857f-148">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。</span><span class="sxs-lookup"><span data-stu-id="5857f-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5857f-149">相關章節</span><span class="sxs-lookup"><span data-stu-id="5857f-149">Related Sections</span></span>  
 [<span data-ttu-id="5857f-150">進階開發技術</span><span class="sxs-lookup"><span data-stu-id="5857f-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="5857f-151">提供與 .NET Framework 中精密的開發工作和技巧有關的詳細資訊之連結。</span><span class="sxs-lookup"><span data-stu-id="5857f-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="5857f-152">使用 ASP.NET 和 XML Web Service 用戶端建立的 XML Web Service</span><span class="sxs-lookup"><span data-stu-id="5857f-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="5857f-153">提供一個主題，說明並解釋如何設計使用 ASP.NET 的 XML Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5857f-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5857f-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5857f-154">See Also</span></span>  
 [<span data-ttu-id="5857f-155">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="5857f-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
