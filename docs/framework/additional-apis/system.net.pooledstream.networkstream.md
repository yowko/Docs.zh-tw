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
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="e8ff7-102">PooledStream. NetworkStream 屬性</span><span class="sxs-lookup"><span data-stu-id="e8ff7-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="e8ff7-103">取得或設定 `PooledStream` 通訊端的網路資料流程。</span><span class="sxs-lookup"><span data-stu-id="e8ff7-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8ff7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8ff7-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="e8ff7-105">屬性值</span><span class="sxs-lookup"><span data-stu-id="e8ff7-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="e8ff7-106">`PooledStream` 通訊端的網路資料流程。</span><span class="sxs-lookup"><span data-stu-id="e8ff7-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ff7-107">備註</span><span class="sxs-lookup"><span data-stu-id="e8ff7-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e8ff7-108">`PooledStream.NetworkStream` 屬性是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="e8ff7-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e8ff7-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ff7-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ff7-110">需求</span><span class="sxs-lookup"><span data-stu-id="e8ff7-110">Requirements</span></span>

<span data-ttu-id="e8ff7-111">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e8ff7-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e8ff7-112">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="e8ff7-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e8ff7-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="e8ff7-113">**.NET Framework versions:** Available since 2.0.</span></span>
