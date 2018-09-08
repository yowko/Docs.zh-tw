---
title: 'How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2edaf7ba540035fbf2f49ba78b41ab99f8889391
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199306"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="9ae37-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span><span class="sxs-lookup"><span data-stu-id="9ae37-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="9ae37-103">XML 結構描述定義工具 (Xsd.exe) 讓您產生說明類別的 XML 結構描述或產生由 XML 結構描述定義的類別。</span><span class="sxs-lookup"><span data-stu-id="9ae37-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="9ae37-104">下列程序將說明如何執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="9ae37-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="9ae37-105">產生符合特定結構描述的類別</span><span class="sxs-lookup"><span data-stu-id="9ae37-105">To generate classes that conform to a specific schema</span></span>  
  
1.  <span data-ttu-id="9ae37-106">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9ae37-106">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="9ae37-107">將 XML 結構描述當成引數傳遞至 XML 結構描述定義工具，以建立一組類別精確地符合 XML 結構描述，例如：</span><span class="sxs-lookup"><span data-stu-id="9ae37-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="9ae37-108">此工具只能處理參考 2001 年 3 月 16 日全球資訊網協會 XML 規格的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9ae37-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="9ae37-109">換句話說，XML 結構描述命名空間必須是"http://www.w3.org/2001/XMLSchema」 在下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ae37-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  <span data-ttu-id="9ae37-110">視需要，使用方法、屬性或欄位來變更類別。</span><span class="sxs-lookup"><span data-stu-id="9ae37-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="9ae37-111">如需使用屬性修改類別的詳細資訊，請參閱[使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)和[控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae37-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="9ae37-112">檢查在序列化一個類別 (或多個類別) 時產生的 XML 資料流結構描述，通常很有用。</span><span class="sxs-lookup"><span data-stu-id="9ae37-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="9ae37-113">例如，您可發佈結構描述供其他人使用，或是將它與一個您想要達到符合性的結構描述比較。</span><span class="sxs-lookup"><span data-stu-id="9ae37-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="9ae37-114">從一組類別產生 XML 結構描述文件</span><span class="sxs-lookup"><span data-stu-id="9ae37-114">To generate an XML Schema document from a set of classes</span></span>  
  
1.  <span data-ttu-id="9ae37-115">將類別編譯為 DLL。</span><span class="sxs-lookup"><span data-stu-id="9ae37-115">Compile the class or classes into a DLL.</span></span>  
  
2.  <span data-ttu-id="9ae37-116">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9ae37-116">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="9ae37-117">將 DLL 當成引數傳遞給 Xsd.exe，例如：</span><span class="sxs-lookup"><span data-stu-id="9ae37-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="9ae37-118">將寫入結構描述，以 "schema0.xsd" 名稱開始。</span><span class="sxs-lookup"><span data-stu-id="9ae37-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae37-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae37-119">See also</span></span>

- <xref:System.Data.DataSet>  
- [<span data-ttu-id="9ae37-120">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="9ae37-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
- [<span data-ttu-id="9ae37-121">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="9ae37-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="9ae37-122">XML 結構描述定義工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="9ae37-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [<span data-ttu-id="9ae37-123">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="9ae37-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [<span data-ttu-id="9ae37-124">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="9ae37-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
