---
title: ICorDebugMemoryBuffer::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c88d389f80b4b3d811d95f65acd41f294d076b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969082"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="a1c9e-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="a1c9e-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="a1c9e-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="a1c9e-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1c9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1c9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1c9e-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="a1c9e-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="a1c9e-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1c9e-107">備註</span><span class="sxs-lookup"><span data-stu-id="a1c9e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1c9e-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="a1c9e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1c9e-109">需求</span><span class="sxs-lookup"><span data-stu-id="a1c9e-109">Requirements</span></span>  
 <span data-ttu-id="a1c9e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c9e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1c9e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1c9e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1c9e-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1c9e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1c9e-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1c9e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c9e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c9e-114">See also</span></span>

- [<span data-ttu-id="a1c9e-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="a1c9e-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a1c9e-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a1c9e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
