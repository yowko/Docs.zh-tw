---
title: ICorDebugMemoryBuffer::GetStartAddress 方法
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f76bf1479db987e4956d8b876f67d629d927f956
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710749"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="efd62-102">ICorDebugMemoryBuffer::GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="efd62-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>

<span data-ttu-id="efd62-103">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="efd62-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd62-104">語法</span><span class="sxs-lookup"><span data-stu-id="efd62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd62-105">參數</span><span class="sxs-lookup"><span data-stu-id="efd62-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="efd62-106">[out] 記憶體緩衝區的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="efd62-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efd62-107">備註</span><span class="sxs-lookup"><span data-stu-id="efd62-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="efd62-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="efd62-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd62-109">需求</span><span class="sxs-lookup"><span data-stu-id="efd62-109">Requirements</span></span>  

 <span data-ttu-id="efd62-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efd62-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd62-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efd62-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efd62-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efd62-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efd62-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd62-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd62-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efd62-114">See also</span></span>

- [<span data-ttu-id="efd62-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="efd62-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="efd62-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="efd62-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
