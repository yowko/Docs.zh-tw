---
title: XmlReader. CreateSqlReader 方法（system.string）
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584131"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader. CreateSqlReader 方法

使用剖析用的指定資料流、設定和內容資訊，建立新的 <xref:System.Xml.XmlReader> 執行個體。

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>參數

- `input` <xref:System.IO.Stream>  
  包含 XML 資料的資料流。

- `settings` <xref:System.Xml.XmlReaderSettings>  
  新 <xref:System.Xml.XmlReader> 執行個體的設定。 這個值可以是 `null`。

- `inputContext` <xref:System.Xml.XmlParserContext>  
  剖析 XML 片段所需的內容資訊。 這個值可以是 `null`。

## <a name="returns"></a>Returns

<xref:System.Xml.XmlReader>  
用以在資料流中讀取 XML 資料的物件。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t_0 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Xml>

**元件：** .Xml .dll

**.NET Framework 版本：** 自2.0 開始提供。
