---
title: ICorDebugMemoryBuffer::GetStartAddress 方法
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422929"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="767bb-102">ICorDebugMemoryBuffer::GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="767bb-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="767bb-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="767bb-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="767bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="767bb-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="767bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="767bb-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="767bb-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="767bb-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="767bb-107">備註</span><span class="sxs-lookup"><span data-stu-id="767bb-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="767bb-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="767bb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="767bb-109">需求</span><span class="sxs-lookup"><span data-stu-id="767bb-109">Requirements</span></span>  
 <span data-ttu-id="767bb-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="767bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="767bb-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="767bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="767bb-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="767bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="767bb-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="767bb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767bb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="767bb-114">See Also</span></span>  
 [<span data-ttu-id="767bb-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="767bb-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="767bb-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="767bb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
