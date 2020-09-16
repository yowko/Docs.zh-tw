---
title: XML 結構描述定義工具和 XML 序列化
description: 'XML 架構定義工具會產生 XSD 架構的 c # 或 Visual Basic 類別檔案，並從程式庫或可執行檔產生 XML 架構。'
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 6451f3b5f6e8ec2c1454e5cf7ffb95a96b620214
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554979"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="1468a-103">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="1468a-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="1468a-104">XML 架構定義工具 ([Xml 架構定義工具 ( # A0) ](xml-schema-definition-tool-xsd-exe.md)) 與 .NET Framework 工具一起安裝，作為 Windows &reg; 軟體發展工具組 (SDK) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1468a-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="1468a-105">該工具的設計主要有兩個目的：</span><span class="sxs-lookup"><span data-stu-id="1468a-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="1468a-106">產生符合特定 XML 結構描述定義語言 (XSD) 結構描述的 C# 或 Visual Basic 類別檔。</span><span class="sxs-lookup"><span data-stu-id="1468a-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="1468a-107">此工具以 XML 結構描述做為引數並輸出包含各種類別的檔案，在以 <xref:System.Xml.Serialization.XmlSerializer> 序列化時，符合結構描述。</span><span class="sxs-lookup"><span data-stu-id="1468a-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="1468a-108">如需如何使用此工具以產生符合特定結構描述之類別的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="1468a-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="1468a-109">從 .dll 檔或 .exe 檔產生 XML 結構描述文件。</span><span class="sxs-lookup"><span data-stu-id="1468a-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="1468a-110">若要檢視您所建立或已修改其中屬性之檔案集的結構描述，請將 DLL 或 EXE 當成引數傳遞至工具以產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1468a-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="1468a-111">如需如何使用工具從類別集產生 XML 結構描述文件的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="1468a-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="1468a-112">如需使用此工具的詳細資訊，請參閱 [XML 架構定義工具 ( # A0) ](xml-schema-definition-tool-xsd-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1468a-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1468a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1468a-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="1468a-114">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="1468a-114">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="1468a-115">XML 架構定義工具 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="1468a-115">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="1468a-116">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="1468a-116">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="1468a-117">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="1468a-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="1468a-118">如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件</span><span class="sxs-lookup"><span data-stu-id="1468a-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](xml-schema-def-tool-gen.md)
- <span data-ttu-id="1468a-119">[XML 結構描述繫結支援](/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1468a-119">[XML Schema Binding Support](/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
