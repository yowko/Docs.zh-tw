---
title: MailBnfHelper 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990310"
---
# <a name="mailbnfhelper-class"></a>MailBnfHelper 類別

包含用來剖析網際網路訊息格式字串的公用程式方法。 這個類別無法被繼承。

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="ascii7bitmaxvalue-field"></a>Ascii7bitMaxValue 欄位

表示最大的7位 Ascii 值。

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a>文字欄位

表示原子中允許的字元。

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a>CR 欄位

表示回車符。

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a>Ctext 欄位

表示批註內允許的字元。

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a>點欄位

表示全停用字元（ `.` ）。

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a>EndComment 欄位

表示指定批註結尾的字元。

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a>LF 欄位

表示換行字元。

```csharp
internal static readonly char LF
```

## <a name="space-field"></a>空間欄位

代表空白字元。

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a>StartComment 欄位

表示指定批註開頭的字元。

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a>Tab 欄位

表示定位字元。

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
