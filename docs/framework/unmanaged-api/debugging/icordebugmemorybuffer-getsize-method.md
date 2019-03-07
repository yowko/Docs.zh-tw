---
title: ICorDebugMemoryBuffer::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdf5e6e52b0c650e56368493074ea7db8e5bac9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485430"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="9d2b1-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9d2b1-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="9d2b1-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9d2b1-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d2b1-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d2b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d2b1-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="9d2b1-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="9d2b1-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d2b1-107">備註</span><span class="sxs-lookup"><span data-stu-id="9d2b1-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d2b1-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="9d2b1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2b1-109">需求</span><span class="sxs-lookup"><span data-stu-id="9d2b1-109">Requirements</span></span>  
 <span data-ttu-id="9d2b1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d2b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d2b1-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d2b1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d2b1-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d2b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d2b1-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d2b1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2b1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d2b1-114">See also</span></span>
- [<span data-ttu-id="9d2b1-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="9d2b1-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="9d2b1-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9d2b1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
