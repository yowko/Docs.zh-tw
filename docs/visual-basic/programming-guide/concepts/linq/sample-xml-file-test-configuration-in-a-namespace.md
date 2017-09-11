---
title: "範例 XML 檔︰ 測試組態中 Namespace3 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: aff02614-30ee-45e1-bc0f-d64b193d20b8
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93a32c80e29d5b78bb4787f5528e3c9ed4bed20e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="5bd4e-102">範例 XML 檔：命名空間中的測試組態</span><span class="sxs-lookup"><span data-stu-id="5bd4e-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="5bd4e-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="5bd4e-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] documentation.</span></span> <span data-ttu-id="5bd4e-104">這是測試組態檔案。</span><span class="sxs-lookup"><span data-stu-id="5bd4e-104">This is a test configuration file.</span></span> <span data-ttu-id="5bd4e-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="5bd4e-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="5bd4e-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="5bd4e-106">TestConfigInNamespace.xml</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5bd4e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd4e-107">See Also</span></span>  
 [<span data-ttu-id="5bd4e-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5bd4e-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
