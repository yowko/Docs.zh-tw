---
title: PrepForRemoting 方法（系統）
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214891"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="f6db7-102">Exception.PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="f6db7-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="f6db7-103">保留伺服器端堆疊追蹤，方法是將它附加至訊息，然後在用戶端呼叫網站重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f6db7-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="f6db7-104">傳回值</span><span class="sxs-lookup"><span data-stu-id="f6db7-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="f6db7-105">這個 <xref:System.Exception> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6db7-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6db7-106">備註</span><span class="sxs-lookup"><span data-stu-id="f6db7-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f6db7-107">`Exception.PrepForRemoting` 方法是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f6db7-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f6db7-108">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f6db7-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6db7-109">需求</span><span class="sxs-lookup"><span data-stu-id="f6db7-109">Requirements</span></span>

<span data-ttu-id="f6db7-110">**命名空間：** <xref:System></span><span class="sxs-lookup"><span data-stu-id="f6db7-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="f6db7-111">**元件：** mscorlib （在 mscorlib.dll 中）</span><span class="sxs-lookup"><span data-stu-id="f6db7-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="f6db7-112">**.NET Framework 版本：** 自1.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="f6db7-112">**.NET Framework versions:** Available since 1.0.</span></span>
