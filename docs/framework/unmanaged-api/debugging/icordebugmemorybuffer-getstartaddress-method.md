---
title: 'Icordebugmemorybuffer:: Getstartaddress 方法'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136977"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="875ab-102">Icordebugmemorybuffer:: Getstartaddress 方法</span><span class="sxs-lookup"><span data-stu-id="875ab-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="875ab-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="875ab-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="875ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="875ab-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="875ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="875ab-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="875ab-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="875ab-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="875ab-107">備註</span><span class="sxs-lookup"><span data-stu-id="875ab-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="875ab-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="875ab-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="875ab-109">需求</span><span class="sxs-lookup"><span data-stu-id="875ab-109">Requirements</span></span>  
 <span data-ttu-id="875ab-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="875ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="875ab-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="875ab-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="875ab-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="875ab-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="875ab-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="875ab-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="875ab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="875ab-114">See also</span></span>

- [<span data-ttu-id="875ab-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="875ab-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="875ab-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="875ab-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
