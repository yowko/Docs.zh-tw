---
title: 如何建置 LINQ to XML 範例
description: '本檔中的 c # 和 Visual Basic 程式碼會使用來自不同命名空間的類別和類型。 若要編譯和執行程式碼，您必須提供適當的指示詞和語句來存取命名空間。'
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 94b2368e2c861f84d7db08fbbba57ef0f0da4d40
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552144"
---
# <a name="how-to-build-linq-to-xml-examples"></a><span data-ttu-id="87a9d-104">如何建置 LINQ to XML 範例</span><span class="sxs-lookup"><span data-stu-id="87a9d-104">How to build LINQ to XML examples</span></span>

<span data-ttu-id="87a9d-105">本檔中的程式碼片段和範例會使用來自不同命名空間的類別和類型。</span><span class="sxs-lookup"><span data-stu-id="87a9d-105">The snippets and examples in this documentation use classes and types from various namespaces.</span></span> <span data-ttu-id="87a9d-106">編譯 c # 程式碼時，您必須提供適當的指示詞 `using` ，而編譯 Visual Basic 程式碼時，您需要提供適當的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="87a9d-106">When compiling C# code you need to supply appropriate `using` directives, and when compiling Visual Basic code you need to supply appropriate `Imports` statements.</span></span>

## <a name="example"></a><span data-ttu-id="87a9d-107">範例</span><span class="sxs-lookup"><span data-stu-id="87a9d-107">Example</span></span>

<span data-ttu-id="87a9d-108">下列程式碼包含 C# 範例建置與執行所需的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="87a9d-108">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="87a9d-109">並非每個範例都需要使用所有 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="87a9d-109">Not all `using` directives are required for every example.</span></span>

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

<span data-ttu-id="87a9d-110">下列程式碼包含 Visual Basic 範例建置與執行所需的 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a9d-110">The following code contains the `Imports` statements that the Visual Basic examples require to build and run.</span></span> <span data-ttu-id="87a9d-111">並非每個範例都需要使用所有 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a9d-111">Not all `Imports` statements are required for every example.</span></span>

```vb
Imports System.Diagnostics
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.Specialized
Imports System.Text
Imports System.Linq
Imports System.Xml
Imports System.Xml.Linq
Imports System.Xml.Schema
Imports System.Xml.XPath
Imports System.Xml.Xsl
Imports System.IO
Imports System.Threading
Imports System.Reflection
Imports System.IO.Packaging
```

## <a name="see-also"></a><span data-ttu-id="87a9d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87a9d-112">See also</span></span>

- [<span data-ttu-id="87a9d-113">LINQ to XML 總覽</span><span class="sxs-lookup"><span data-stu-id="87a9d-113">LINQ to XML overview</span></span>](linq-xml-overview.md)
