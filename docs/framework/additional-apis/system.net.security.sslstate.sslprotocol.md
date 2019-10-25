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
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="ec263-102">SslState. SslProtocol 屬性</span><span class="sxs-lookup"><span data-stu-id="ec263-102">SslState.SslProtocol Property</span></span>

<span data-ttu-id="ec263-103">取得 SSL 通訊協定版本。</span><span class="sxs-lookup"><span data-stu-id="ec263-103">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec263-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec263-104">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="ec263-105">屬性值</span><span class="sxs-lookup"><span data-stu-id="ec263-105">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="ec263-106">指定 SSL 通訊協定版本之列舉值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="ec263-106">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec263-107">備註</span><span class="sxs-lookup"><span data-stu-id="ec263-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ec263-108">`SslState.SslProtocol` 屬性是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="ec263-108">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ec263-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="ec263-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec263-110">需求</span><span class="sxs-lookup"><span data-stu-id="ec263-110">Requirements</span></span>

<span data-ttu-id="ec263-111">**命名空間︰** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="ec263-111">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="ec263-112">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="ec263-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ec263-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="ec263-113">**.NET Framework versions:** Available since 2.0.</span></span>
