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
ms.openlocfilehash: f62cbdc4b3e73f0c27492f7ed20b35378654d399
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152954"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="02fe0-102">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="02fe0-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="02fe0-103">提供方法來查詢的方法執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="02fe0-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="02fe0-104">方法</span><span class="sxs-lookup"><span data-stu-id="02fe0-104">Methods</span></span>

| <span data-ttu-id="02fe0-105">方法</span><span class="sxs-lookup"><span data-stu-id="02fe0-105">Method</span></span>                                                                                                                  | <span data-ttu-id="02fe0-106">描述</span><span class="sxs-lookup"><span data-stu-id="02fe0-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="02fe0-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="02fe0-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="02fe0-108">取得地址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="02fe0-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="02fe0-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="02fe0-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="02fe0-110">取得所有可能的進入點之方法的原生編譯的最具代表性的進入點位址。</span><span class="sxs-lookup"><span data-stu-id="02fe0-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="02fe0-111">備註</span><span class="sxs-lookup"><span data-stu-id="02fe0-111">Remarks</span></span>

<span data-ttu-id="02fe0-112">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="02fe0-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="02fe0-113">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="02fe0-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="02fe0-114">需求</span><span class="sxs-lookup"><span data-stu-id="02fe0-114">Requirements</span></span>

<span data-ttu-id="02fe0-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02fe0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="02fe0-116">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="02fe0-116">**Header:** None</span></span>  
<span data-ttu-id="02fe0-117">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="02fe0-117">**Library:** None</span></span>  
**<span data-ttu-id="02fe0-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="02fe0-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="02fe0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02fe0-119">See also</span></span>

- [<span data-ttu-id="02fe0-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="02fe0-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="02fe0-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="02fe0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
