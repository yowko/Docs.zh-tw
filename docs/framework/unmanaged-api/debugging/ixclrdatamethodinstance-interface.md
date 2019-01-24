---
title: IXCLRDataMethodInstance 介面
ms.date: 01/16/2019
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
ms.openlocfilehash: 0eef69cea9f59911b5076f56579b0192be357431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659107"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="da825-102">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="da825-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="da825-103">提供方法來查詢的方法執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="da825-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="da825-104">方法</span><span class="sxs-lookup"><span data-stu-id="da825-104">Methods</span></span>

| <span data-ttu-id="da825-105">方法</span><span class="sxs-lookup"><span data-stu-id="da825-105">Method</span></span>                                                                                                                  | <span data-ttu-id="da825-106">描述</span><span class="sxs-lookup"><span data-stu-id="da825-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="da825-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="da825-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="da825-108">取得地址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="da825-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="da825-109">備註</span><span class="sxs-lookup"><span data-stu-id="da825-109">Remarks</span></span>

<span data-ttu-id="da825-110">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="da825-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="da825-111">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="da825-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="da825-112">需求</span><span class="sxs-lookup"><span data-stu-id="da825-112">Requirements</span></span>

<span data-ttu-id="da825-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da825-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="da825-114">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="da825-114">**Header:** None</span></span>  
<span data-ttu-id="da825-115">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="da825-115">**Library:** None</span></span>  
<span data-ttu-id="da825-116">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="da825-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="da825-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da825-117">See also</span></span>

- [<span data-ttu-id="da825-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="da825-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="da825-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="da825-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
