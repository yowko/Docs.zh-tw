---
title: 如何建立 LINQ to XML 範例（C#）
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 289a13daed7e3c871156bf50c6fa04c113c0cd13
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141462"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="bd07f-102">如何建立 LINQ to XML 範例（C#）</span><span class="sxs-lookup"><span data-stu-id="bd07f-102">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="bd07f-103">此文件中的各種片段與範例使用各種命名空間中的類別和型別。</span><span class="sxs-lookup"><span data-stu-id="bd07f-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="bd07f-104">編譯 C# 程式碼時，您必須提供適當的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="bd07f-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd07f-105">範例</span><span class="sxs-lookup"><span data-stu-id="bd07f-105">Example</span></span>  
 <span data-ttu-id="bd07f-106">下列程式碼包含 C# 範例建置與執行所需的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="bd07f-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="bd07f-107">並非每個範例都需要使用所有 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="bd07f-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd07f-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd07f-108">See also</span></span>

- [<span data-ttu-id="bd07f-109">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd07f-109">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
