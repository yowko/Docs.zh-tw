---
title: ICorDebugMergedAssemblyRecord 介面
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180462"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="7a267-102">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="7a267-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="7a267-103">提供合併組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7a267-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a267-104">方法</span><span class="sxs-lookup"><span data-stu-id="7a267-104">Methods</span></span>  
  
|<span data-ttu-id="7a267-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a267-105">Method</span></span>|<span data-ttu-id="7a267-106">描述</span><span class="sxs-lookup"><span data-stu-id="7a267-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a267-107">GetCulture 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="7a267-108">取得組件的文化特性名稱字串。</span><span class="sxs-lookup"><span data-stu-id="7a267-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="7a267-109">GetIndex 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="7a267-110">取得組件的前置詞索引。</span><span class="sxs-lookup"><span data-stu-id="7a267-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="7a267-111">GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="7a267-112">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="7a267-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="7a267-113">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="7a267-114">取得組件的公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7a267-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="7a267-115">GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="7a267-116">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="7a267-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="7a267-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="7a267-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="7a267-118">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="7a267-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a267-119">備註</span><span class="sxs-lookup"><span data-stu-id="7a267-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a267-120">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="7a267-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7a267-121">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="7a267-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a267-122">需求</span><span class="sxs-lookup"><span data-stu-id="7a267-122">Requirements</span></span>  
 <span data-ttu-id="7a267-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a267-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a267-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a267-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a267-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a267-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a267-126">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a267-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a267-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a267-127">See also</span></span>

- [<span data-ttu-id="7a267-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7a267-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7a267-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="7a267-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
