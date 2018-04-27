---
title: XML 結構描述定義工具和 XML 序列化
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 502218ec2795fcf3cf166edc8ee0852dd6b3a5d1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="4adfd-102">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="4adfd-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="4adfd-103">XML 結構描述定義工具 ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) 會隨 .NET Framework 工具當作 Windows® 軟體開發套件 (SDK) 的一部分安裝。</span><span class="sxs-lookup"><span data-stu-id="4adfd-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="4adfd-104">該工具的設計主要有兩個目的：</span><span class="sxs-lookup"><span data-stu-id="4adfd-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="4adfd-105">產生符合特定 XML 結構描述定義語言 (XSD) 結構描述的 C# 或 Visual Basic 類別檔。</span><span class="sxs-lookup"><span data-stu-id="4adfd-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="4adfd-106">此工具以 XML 結構描述做為引數並輸出包含各種類別的檔案，在以 <xref:System.Xml.Serialization.XmlSerializer> 序列化時，符合結構描述。</span><span class="sxs-lookup"><span data-stu-id="4adfd-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="4adfd-107">如需如何使用此工具以產生符合特定結構描述之類別的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="4adfd-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="4adfd-108">從 .dll 檔或 .exe 檔產生 XML 結構描述文件。</span><span class="sxs-lookup"><span data-stu-id="4adfd-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="4adfd-109">若要檢視您所建立或已修改其中屬性之檔案集的結構描述，請將 DLL 或 EXE 當成引數傳遞至工具以產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4adfd-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="4adfd-110">如需如何使用工具從類別集產生 XML 結構描述文件的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="4adfd-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="4adfd-111">如需這項工具和其他工具的詳細資訊，請參閱[工具](../../../docs/framework/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4adfd-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="4adfd-112">如需工具選項的資訊，請參閱 [XML 結構描述定義工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="4adfd-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adfd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4adfd-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="4adfd-114">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="4adfd-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="4adfd-115">XML 結構描述定義工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="4adfd-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="4adfd-116">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="4adfd-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="4adfd-117">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="4adfd-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="4adfd-118">如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件</span><span class="sxs-lookup"><span data-stu-id="4adfd-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="4adfd-119">.NET Framework 中的 XML 結構描述繫結支援</span><span class="sxs-lookup"><span data-stu-id="4adfd-119">XML Schema Binding Support in the .NET Framework</span></span>](https://msdn.microsoft.com/library/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
