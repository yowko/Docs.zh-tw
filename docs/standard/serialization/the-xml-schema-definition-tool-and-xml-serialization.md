---
title: XML 結構描述定義工具和 XML 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588394"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="9645d-102">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="9645d-102">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="9645d-103">XML 架構定義工具[(XML 架構定義工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)與 .NET&reg;框架工具一起安裝,作為 Windows 軟體開發工具套件 (SDK) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="9645d-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="9645d-104">該工具的設計主要有兩個目的：</span><span class="sxs-lookup"><span data-stu-id="9645d-104">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="9645d-105">產生符合特定 XML 結構描述定義語言 (XSD) 結構描述的 C# 或 Visual Basic 類別檔。</span><span class="sxs-lookup"><span data-stu-id="9645d-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="9645d-106">此工具以 XML 結構描述做為引數並輸出包含各種類別的檔案，在以 <xref:System.Xml.Serialization.XmlSerializer> 序列化時，符合結構描述。</span><span class="sxs-lookup"><span data-stu-id="9645d-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="9645d-107">如需如何使用此工具以產生符合特定結構描述之類別的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="9645d-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="9645d-108">從 .dll 檔或 .exe 檔產生 XML 結構描述文件。</span><span class="sxs-lookup"><span data-stu-id="9645d-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="9645d-109">若要檢視您所建立或已修改其中屬性之檔案集的結構描述，請將 DLL 或 EXE 當成引數傳遞至工具以產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="9645d-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="9645d-110">如需如何使用工具從類別集產生 XML 結構描述文件的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="9645d-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="9645d-111">有關使用該工具的詳細資訊,請參閱 XML[架構定義工具 (Xsd.exe)。](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)</span><span class="sxs-lookup"><span data-stu-id="9645d-111">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9645d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9645d-112">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="9645d-113">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="9645d-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="9645d-114">XML 結構描述定義工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="9645d-114">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="9645d-115">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="9645d-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="9645d-116">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="9645d-116">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="9645d-117">如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件</span><span class="sxs-lookup"><span data-stu-id="9645d-117">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="9645d-118">[XML 結構描述繫結支援](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9645d-118">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
