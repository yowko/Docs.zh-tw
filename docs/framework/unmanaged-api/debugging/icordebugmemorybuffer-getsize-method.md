---
title: ICorDebugMemoryBuffer::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5984addb41c33468068f7ad24a15533f75dc367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714720"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="aa779-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="aa779-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="aa779-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="aa779-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa779-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa779-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa779-105">參數</span><span class="sxs-lookup"><span data-stu-id="aa779-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="aa779-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="aa779-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa779-107">備註</span><span class="sxs-lookup"><span data-stu-id="aa779-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa779-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="aa779-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa779-109">需求</span><span class="sxs-lookup"><span data-stu-id="aa779-109">Requirements</span></span>  
 <span data-ttu-id="aa779-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa779-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa779-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa779-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa779-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa779-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa779-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa779-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa779-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa779-114">See also</span></span>
- [<span data-ttu-id="aa779-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="aa779-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="aa779-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aa779-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
