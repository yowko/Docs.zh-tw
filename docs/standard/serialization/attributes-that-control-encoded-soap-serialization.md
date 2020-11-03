---
title: 控制編碼 SOAP 序列化的屬性
description: 本文列出在 System.Xml 中找到的一組特殊屬性。符合 SOAP 規格所需的序列化命名空間。
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 69a9d1c8734a393b576cf87e7e05ef92c10120c8
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282033"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="26504-103">控制編碼 SOAP 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="26504-103">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="26504-104">全球資訊網協會 (的 W3C) 檔（名為 [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) ）包含選擇性區段 (第5節) ，其中描述 soap 參數的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="26504-104">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="26504-105">若要遵循第 5 節的規格，您必須使用在 <xref:System.Xml.Serialization> 命名空間中的特殊屬性集。</span><span class="sxs-lookup"><span data-stu-id="26504-105">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="26504-106">套用適合類別與類別成員的那些屬性，然後使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="26504-106">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="26504-107">下表顯示屬性、其可套用位置及作用。</span><span class="sxs-lookup"><span data-stu-id="26504-107">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="26504-108">如需使用這些屬性來控制 XML 序列化的詳細資訊，請參閱[如何：將物件序列化為 SOAP 編碼的 XML 資料流](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)和[如何：覆寫編碼的 SOAP XML 序列化](how-to-override-encoded-soap-xml-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="26504-108">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="26504-109">如需屬性的詳細資訊，請參閱[屬性](../attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="26504-109">For more information about attributes, see [Attributes](../attributes/index.md).</span></span>

|<span data-ttu-id="26504-110">屬性</span><span class="sxs-lookup"><span data-stu-id="26504-110">Attribute</span></span>|<span data-ttu-id="26504-111">適用於</span><span class="sxs-lookup"><span data-stu-id="26504-111">Applies to</span></span>|<span data-ttu-id="26504-112">指定</span><span class="sxs-lookup"><span data-stu-id="26504-112">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="26504-113">公用欄位、屬性、參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="26504-113">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="26504-114">類別成員將會序列化成 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="26504-114">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="26504-115">公用欄位、屬性、參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="26504-115">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="26504-116">類別將會序列化成 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="26504-116">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="26504-117">為列舉識別項的公用欄位。</span><span class="sxs-lookup"><span data-stu-id="26504-117">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="26504-118">列舉成員的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="26504-118">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="26504-119">公用屬性與欄位。</span><span class="sxs-lookup"><span data-stu-id="26504-119">Public properties and fields.</span></span>|<span data-ttu-id="26504-120">所屬類別序列化時，略過屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="26504-120">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="26504-121">公用衍生類別宣告以及 Web 服務描述語言 (WSDL) 文件的公用方法。</span><span class="sxs-lookup"><span data-stu-id="26504-121">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="26504-122">當產生結構描述時應包含型別 (在序列化時辨認)。</span><span class="sxs-lookup"><span data-stu-id="26504-122">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="26504-123">公用類別宣告</span><span class="sxs-lookup"><span data-stu-id="26504-123">Public class declarations.</span></span>|<span data-ttu-id="26504-124">類別應序列化成 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="26504-124">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="26504-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26504-125">See also</span></span>

- [<span data-ttu-id="26504-126">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="26504-126">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="26504-127">HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流</span><span class="sxs-lookup"><span data-stu-id="26504-127">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="26504-128">如何：覆寫已編碼的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="26504-128">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="26504-129">屬性</span><span class="sxs-lookup"><span data-stu-id="26504-129">Attributes</span></span>](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="26504-130">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="26504-130">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="26504-131">HOW TO：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="26504-131">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
