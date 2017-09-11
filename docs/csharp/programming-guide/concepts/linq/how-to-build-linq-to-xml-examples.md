---
title: "如何：建置 LINQ to XML 範例 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d95748a69ac42f1c767dcf19c9f6d2edc8c872ee
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="7e6e3-102">如何：建置 LINQ to XML 範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e6e3-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="7e6e3-103">此文件中的各種片段與範例使用各種命名空間中的類別和型別。</span><span class="sxs-lookup"><span data-stu-id="7e6e3-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="7e6e3-104">編譯 C# 程式碼時，您必須提供適當的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="7e6e3-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e6e3-105">範例</span><span class="sxs-lookup"><span data-stu-id="7e6e3-105">Example</span></span>  
 <span data-ttu-id="7e6e3-106">下列程式碼包含 C# 範例建置與執行所需的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="7e6e3-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="7e6e3-107">並非每個範例都需要使用所有 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="7e6e3-107">Not all `using` directives are required for every example.</span></span>  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e6e3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e6e3-108">See Also</span></span>  
 [<span data-ttu-id="7e6e3-109">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e6e3-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

