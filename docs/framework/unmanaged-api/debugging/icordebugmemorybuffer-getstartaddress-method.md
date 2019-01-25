---
title: ICorDebugMemoryBuffer::GetStartAddress 方法
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29149ceb155cdfdf7b735d6939809e80f2ba4dc0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695539"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="bc4e1-102">ICorDebugMemoryBuffer::GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="bc4e1-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="bc4e1-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="bc4e1-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc4e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc4e1-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc4e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc4e1-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bc4e1-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="bc4e1-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc4e1-107">備註</span><span class="sxs-lookup"><span data-stu-id="bc4e1-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bc4e1-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="bc4e1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc4e1-109">需求</span><span class="sxs-lookup"><span data-stu-id="bc4e1-109">Requirements</span></span>  
 <span data-ttu-id="bc4e1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc4e1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc4e1-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc4e1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc4e1-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc4e1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc4e1-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc4e1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4e1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc4e1-114">See also</span></span>
- [<span data-ttu-id="bc4e1-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="bc4e1-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="bc4e1-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bc4e1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
