---
title: ICorDebugMemoryBuffer::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1bef2e2d0e1a1cef74c7568fdd2e9b7986500488
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212601"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="05c55-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="05c55-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="05c55-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="05c55-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c55-104">語法</span><span class="sxs-lookup"><span data-stu-id="05c55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05c55-105">參數</span><span class="sxs-lookup"><span data-stu-id="05c55-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="05c55-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="05c55-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05c55-107">備註</span><span class="sxs-lookup"><span data-stu-id="05c55-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05c55-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="05c55-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c55-109">需求</span><span class="sxs-lookup"><span data-stu-id="05c55-109">Requirements</span></span>  
 <span data-ttu-id="05c55-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05c55-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c55-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05c55-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05c55-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05c55-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05c55-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c55-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c55-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="05c55-114">See also</span></span>

- [<span data-ttu-id="05c55-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="05c55-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="05c55-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="05c55-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
