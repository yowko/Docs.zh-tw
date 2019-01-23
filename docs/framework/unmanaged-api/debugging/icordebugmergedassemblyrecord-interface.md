---
title: ICorDebugMergedAssemblyRecord 介面
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f42b8d6eb1a35052b25fda6e7cc9c7d00836df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559355"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="656cb-102">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="656cb-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="656cb-103">提供合併之組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="656cb-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="656cb-104">方法</span><span class="sxs-lookup"><span data-stu-id="656cb-104">Methods</span></span>  
  
|<span data-ttu-id="656cb-105">方法</span><span class="sxs-lookup"><span data-stu-id="656cb-105">Method</span></span>|<span data-ttu-id="656cb-106">描述</span><span class="sxs-lookup"><span data-stu-id="656cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="656cb-107">GetCulture 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="656cb-108">取得組件的文化特性名稱字串。</span><span class="sxs-lookup"><span data-stu-id="656cb-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="656cb-109">GetIndex 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="656cb-110">取得組件的前置詞索引。</span><span class="sxs-lookup"><span data-stu-id="656cb-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="656cb-111">GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="656cb-112">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="656cb-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="656cb-113">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="656cb-114">取得組件的公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="656cb-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="656cb-115">GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="656cb-116">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="656cb-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="656cb-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="656cb-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="656cb-118">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="656cb-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="656cb-119">備註</span><span class="sxs-lookup"><span data-stu-id="656cb-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="656cb-120">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="656cb-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="656cb-121">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="656cb-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656cb-122">需求</span><span class="sxs-lookup"><span data-stu-id="656cb-122">Requirements</span></span>  
 <span data-ttu-id="656cb-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="656cb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656cb-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="656cb-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="656cb-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="656cb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="656cb-126">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656cb-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656cb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="656cb-127">See also</span></span>
- [<span data-ttu-id="656cb-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="656cb-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="656cb-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="656cb-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
