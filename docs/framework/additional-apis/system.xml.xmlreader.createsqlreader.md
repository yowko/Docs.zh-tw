---
title: XmlReader.createSqlReader 方法（系統.Xml）
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155735"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader 方法

使用剖析用的指定資料流、設定和內容資訊，建立新的 <xref:System.Xml.XmlReader> 執行個體。

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>參數

- `input` <xref:System.IO.Stream>  
  包含 XML 資料的資料流。

- `settings` <xref:System.Xml.XmlReaderSettings>  
  新 <xref:System.Xml.XmlReader> 執行個體的設定。 此值可以是 `null`。

- `inputContext` <xref:System.Xml.XmlParserContext>  
  剖析 XML 片段所需的內容資訊。 此值可以是 `null`。

## <a name="returns"></a>傳回值

<xref:System.Xml.XmlReader>  
用以在資料流中讀取 XML 資料的物件。

## <a name="remarks"></a>備註

> [!WARNING]
> 該方法`XmlReader.CreateSqlReader`是內部的，不用於直接在代碼中使用。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Xml>

**裝配：** 系統.Xml.dll

**.NET 框架版本：** 自 2.0 起可用。
