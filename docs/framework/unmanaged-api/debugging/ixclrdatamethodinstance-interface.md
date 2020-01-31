---
title: IXCLRDataMethodInstance 介面
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790415"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="44646-102">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="44646-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="44646-103">提供查詢方法實例相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="44646-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="44646-104">方法</span><span class="sxs-lookup"><span data-stu-id="44646-104">Methods</span></span>

| <span data-ttu-id="44646-105">方法</span><span class="sxs-lookup"><span data-stu-id="44646-105">Method</span></span>                                                                                                                  | <span data-ttu-id="44646-106">描述</span><span class="sxs-lookup"><span data-stu-id="44646-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="44646-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="44646-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="44646-108">取得用來定址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="44646-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="44646-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="44646-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="44646-110">針對方法的所有可能進入點的原生編譯，取得最具代表性的進入點位址。</span><span class="sxs-lookup"><span data-stu-id="44646-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="44646-111">備註</span><span class="sxs-lookup"><span data-stu-id="44646-111">Remarks</span></span>

<span data-ttu-id="44646-112">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="44646-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="44646-113">不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` 可透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="44646-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="44646-114">需求</span><span class="sxs-lookup"><span data-stu-id="44646-114">Requirements</span></span>

<span data-ttu-id="44646-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44646-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="44646-116">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="44646-116">**Header:** None</span></span>  
<span data-ttu-id="44646-117">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="44646-117">**Library:** None</span></span>  
<span data-ttu-id="44646-118">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="44646-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="44646-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="44646-119">See also</span></span>

- [<span data-ttu-id="44646-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="44646-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="44646-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="44646-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
