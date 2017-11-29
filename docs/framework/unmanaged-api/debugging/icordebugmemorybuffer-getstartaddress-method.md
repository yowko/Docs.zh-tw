---
title: "ICorDebugMemoryBuffer::GetStartAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97c08e87f63b36bfee5ade75e44f4867441bee92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="48bff-102">ICorDebugMemoryBuffer::GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="48bff-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="48bff-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="48bff-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48bff-104">語法</span><span class="sxs-lookup"><span data-stu-id="48bff-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48bff-105">參數</span><span class="sxs-lookup"><span data-stu-id="48bff-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="48bff-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="48bff-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48bff-107">備註</span><span class="sxs-lookup"><span data-stu-id="48bff-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="48bff-108">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="48bff-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48bff-109">需求</span><span class="sxs-lookup"><span data-stu-id="48bff-109">Requirements</span></span>  
 <span data-ttu-id="48bff-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48bff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48bff-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48bff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48bff-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48bff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48bff-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48bff-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48bff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48bff-114">See Also</span></span>  
 [<span data-ttu-id="48bff-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="48bff-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="48bff-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="48bff-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
