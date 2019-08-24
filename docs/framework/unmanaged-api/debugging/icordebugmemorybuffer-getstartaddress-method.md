---
title: 'ICorDebugMemoryBuffer:: GetStartAddress 方法'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1394624051baa9e7dd21e29788d5fab28332081b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987555"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="22910-102">ICorDebugMemoryBuffer:: GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="22910-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="22910-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="22910-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22910-104">語法</span><span class="sxs-lookup"><span data-stu-id="22910-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22910-105">參數</span><span class="sxs-lookup"><span data-stu-id="22910-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="22910-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="22910-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22910-107">備註</span><span class="sxs-lookup"><span data-stu-id="22910-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="22910-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="22910-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22910-109">需求</span><span class="sxs-lookup"><span data-stu-id="22910-109">Requirements</span></span>  
 <span data-ttu-id="22910-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22910-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22910-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22910-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22910-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22910-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22910-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22910-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22910-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22910-114">See also</span></span>

- [<span data-ttu-id="22910-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="22910-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="22910-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="22910-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
