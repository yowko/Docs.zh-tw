---
title: MailAddressParser 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990315"
---
# <a name="mailaddressparser-class"></a>MailAddressParser 類別

剖析 RFC 2822 中所述的電子郵件地址。 這個類別無法被繼承。

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="parseaddress-method"></a>ParseAddress 方法

剖析指定之字串中的單一電子郵件地址。

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>參數

`data` <xref:System.String>

包含要剖析之電子郵件地址的字串。

### <a name="return-value"></a>傳回值

<xref:System.Net.Mail.MailAddress>

有效的電子郵件地址。

### <a name="exceptions"></a>例外狀況

<xref:System.FormatException?displayProperty=nameWithType>

電子郵件地址無效。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
