---
title: SslState. SslProtocol 屬性（系統 .Net. 安全性）
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847196"
---
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol 屬性

取得 SSL 通訊協定版本。

## <a name="syntax"></a>語法

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>屬性值

<xref:System.Security.Authentication.SslProtocols>  
指定 SSL 通訊協定版本之列舉值的位元組合。

## <a name="remarks"></a>備註

> [!WARNING]
> `SslState.SslProtocol` 屬性是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Net.Security>

**元件：** 系統（在 System .dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
