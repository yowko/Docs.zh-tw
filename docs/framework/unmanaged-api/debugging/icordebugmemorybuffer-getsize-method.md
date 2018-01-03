---
title: "ICorDebugMemoryBuffer::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658fb2ce289b4b8cabfcf0cc2ea5f8dace2ec754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="b316f-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="b316f-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="b316f-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b316f-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b316f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b316f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b316f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b316f-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="b316f-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="b316f-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b316f-107">備註</span><span class="sxs-lookup"><span data-stu-id="b316f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b316f-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="b316f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b316f-109">需求</span><span class="sxs-lookup"><span data-stu-id="b316f-109">Requirements</span></span>  
 <span data-ttu-id="b316f-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b316f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b316f-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b316f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b316f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b316f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b316f-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b316f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b316f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b316f-114">See Also</span></span>  
 [<span data-ttu-id="b316f-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="b316f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="b316f-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b316f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
