---
title: 'How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents'
description: 瞭解如何使用 XML 架構定義工具來產生 XML 架構，以描述類別或產生 XML 架構所定義的類別。
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 9d94ed7c2558b1d60efb8b3cdbaac1ea1f0087b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676656"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="30cc0-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span><span class="sxs-lookup"><span data-stu-id="30cc0-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>

<span data-ttu-id="30cc0-104">XML 結構描述定義工具 (Xsd.exe) 讓您產生說明類別的 XML 結構描述或產生由 XML 結構描述定義的類別。</span><span class="sxs-lookup"><span data-stu-id="30cc0-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="30cc0-105">下列程序將說明如何執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="30cc0-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="30cc0-106">XML 架構定義工具 ( # A0) 通常可以在下列路徑中找到： </span><span class="sxs-lookup"><span data-stu-id="30cc0-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="30cc0-107">_C： \\ Program Files (x86) \\ Microsoft sdk \\ Windows \\ {version} \\ Bin \\ NETFX {version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="30cc0-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="30cc0-108">產生符合特定結構描述的類別</span><span class="sxs-lookup"><span data-stu-id="30cc0-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="30cc0-109">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="30cc0-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="30cc0-110">將 XML 結構描述當成引數傳遞至 XML 結構描述定義工具，以建立一組類別精確地符合 XML 結構描述，例如：</span><span class="sxs-lookup"><span data-stu-id="30cc0-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="30cc0-111">此工具只能處理參考 2001 年 3 月 16 日全球資訊網協會 XML 規格的結構描述。</span><span class="sxs-lookup"><span data-stu-id="30cc0-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="30cc0-112">換句話說，XML 架構命名空間必須是 ""， http://www.w3.org/2001/XMLSchema 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30cc0-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="30cc0-113">視需要，使用方法、屬性或欄位來變更類別。</span><span class="sxs-lookup"><span data-stu-id="30cc0-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="30cc0-114">如需使用屬性修改類別的詳細資訊，請參閱[使用屬性控制 XML 序列化](controlling-xml-serialization-using-attributes.md)和[控制編碼 SOAP 序列化的屬性](attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="30cc0-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="30cc0-115">檢查在序列化一個類別 (或多個類別) 時產生的 XML 資料流結構描述，通常很有用。</span><span class="sxs-lookup"><span data-stu-id="30cc0-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="30cc0-116">例如，您可發佈結構描述供其他人使用，或是將它與一個您想要達到符合性的結構描述比較。</span><span class="sxs-lookup"><span data-stu-id="30cc0-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="30cc0-117">從一組類別產生 XML 結構描述文件</span><span class="sxs-lookup"><span data-stu-id="30cc0-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="30cc0-118">將類別編譯為 DLL。</span><span class="sxs-lookup"><span data-stu-id="30cc0-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="30cc0-119">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="30cc0-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="30cc0-120">將 DLL 當成引數傳遞給 Xsd.exe，例如：</span><span class="sxs-lookup"><span data-stu-id="30cc0-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="30cc0-121">將寫入結構描述，以 "schema0.xsd" 名稱開始。</span><span class="sxs-lookup"><span data-stu-id="30cc0-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cc0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30cc0-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="30cc0-123">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="30cc0-123">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="30cc0-124">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="30cc0-124">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="30cc0-125">XML 架構定義工具 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="30cc0-125">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="30cc0-126">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="30cc0-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="30cc0-127">HOW TO：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="30cc0-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
