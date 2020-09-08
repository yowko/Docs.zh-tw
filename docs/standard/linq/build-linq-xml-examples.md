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
# <a name="how-to-build-linq-to-xml-examples"></a>如何建置 LINQ to XML 範例

本檔中的程式碼片段和範例會使用來自不同命名空間的類別和類型。 編譯 c # 程式碼時，您必須提供適當的指示詞 `using` ，而編譯 Visual Basic 程式碼時，您需要提供適當的 `Imports` 語句。

## <a name="example"></a>範例

下列程式碼包含 C# 範例建置與執行所需的 `using` 指示詞。 並非每個範例都需要使用所有 `using` 指示詞。

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

下列程式碼包含 Visual Basic 範例建置與執行所需的 `Imports` 陳述式。 並非每個範例都需要使用所有 `Imports` 陳述式。

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

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
