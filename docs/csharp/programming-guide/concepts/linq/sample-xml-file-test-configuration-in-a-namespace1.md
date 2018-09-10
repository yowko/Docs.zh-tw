---
title: XML 檔範例：命名空間中的測試組態
ms.date: 07/20/2015
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
ms.openlocfilehash: 01470a66ac42eb9fd68fdcde0d0a4bf9150e3d5f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506497"
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="9e4bb-102">範例 XML 檔：命名空間中的測試組態</span><span class="sxs-lookup"><span data-stu-id="9e4bb-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="9e4bb-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="9e4bb-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="9e4bb-104">這是測試組態檔案。</span><span class="sxs-lookup"><span data-stu-id="9e4bb-104">This is a test configuration file.</span></span> <span data-ttu-id="9e4bb-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="9e4bb-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="9e4bb-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="9e4bb-106">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e4bb-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4bb-107">See Also</span></span>

- [<span data-ttu-id="9e4bb-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9e4bb-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
