---
title: ICorDebugMergedAssemblyRecord 介面
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765410"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="bf87a-102">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="bf87a-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="bf87a-103">提供合併組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf87a-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf87a-104">方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-104">Methods</span></span>  
  
|<span data-ttu-id="bf87a-105">方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-105">Method</span></span>|<span data-ttu-id="bf87a-106">描述</span><span class="sxs-lookup"><span data-stu-id="bf87a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf87a-107">GetCulture 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="bf87a-108">取得組件的文化特性名稱字串。</span><span class="sxs-lookup"><span data-stu-id="bf87a-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="bf87a-109">GetIndex 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="bf87a-110">取得組件的前置詞索引。</span><span class="sxs-lookup"><span data-stu-id="bf87a-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="bf87a-111">GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="bf87a-112">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="bf87a-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="bf87a-113">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="bf87a-114">取得組件的公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="bf87a-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="bf87a-115">GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="bf87a-116">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="bf87a-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="bf87a-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="bf87a-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="bf87a-118">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="bf87a-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf87a-119">備註</span><span class="sxs-lookup"><span data-stu-id="bf87a-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf87a-120">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="bf87a-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bf87a-121">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="bf87a-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf87a-122">需求</span><span class="sxs-lookup"><span data-stu-id="bf87a-122">Requirements</span></span>  
 <span data-ttu-id="bf87a-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf87a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf87a-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf87a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf87a-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf87a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf87a-126">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf87a-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf87a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf87a-127">See also</span></span>

- [<span data-ttu-id="bf87a-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bf87a-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bf87a-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="bf87a-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
