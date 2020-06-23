---
title: PrepForRemoting 方法（系統）
description: 請參閱 .NET 中的 PrepForRemoting 方法。 方法會在用戶端重新擲回例外狀況之前，將伺服器端堆疊追蹤加入至訊息。
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105264"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="a1b53-104">Exception.PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="a1b53-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="a1b53-105">保留伺服器端堆疊追蹤，方法是將它附加至訊息，然後在用戶端呼叫網站重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1b53-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="a1b53-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1b53-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="a1b53-107">這個 <xref:System.Exception> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1b53-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1b53-108">備註</span><span class="sxs-lookup"><span data-stu-id="a1b53-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a1b53-109">`Exception.PrepForRemoting`方法是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="a1b53-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a1b53-110">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="a1b53-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1b53-111">需求</span><span class="sxs-lookup"><span data-stu-id="a1b53-111">Requirements</span></span>

<span data-ttu-id="a1b53-112">**命名空間：** <xref:System></span><span class="sxs-lookup"><span data-stu-id="a1b53-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="a1b53-113">**元件：** mscorlib.dll （在 mscorlib.dll 中）</span><span class="sxs-lookup"><span data-stu-id="a1b53-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="a1b53-114">**.NET Framework 版本：** 自1.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="a1b53-114">**.NET Framework versions:** Available since 1.0.</span></span>
