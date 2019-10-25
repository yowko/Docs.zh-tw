---
title: PooledStream. NetworkStream 屬性（System.Net）
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847175"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream 屬性

取得或設定 `PooledStream` 通訊端的網路資料流程。

## <a name="syntax"></a>語法

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>屬性值

<xref:System.Net.Sockets.NetworkStream>  
`PooledStream` 通訊端的網路資料流程。

## <a name="remarks"></a>備註

> [!WARNING]
> `PooledStream.NetworkStream` 屬性是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Net>

**元件：** 系統（在 System .dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
