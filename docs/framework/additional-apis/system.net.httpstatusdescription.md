---
title: HttpStatusDescription 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990336"
---
# <a name="httpstatusdescription-class"></a>HttpStatusDescription 類別

提供標準 HTTP 狀態原因。 這個類別無法被繼承。

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="get-method"></a>Get 方法

傳回與指定的 HTTP 狀態碼相關聯的描述。

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>參數

`code` <xref:System.Int32>

HTTP 狀態碼，例如 `404` 。

### <a name="return-value"></a>傳回值

<xref:System.String?displayProperty=nameWithType>

HTTP 狀態原因。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
