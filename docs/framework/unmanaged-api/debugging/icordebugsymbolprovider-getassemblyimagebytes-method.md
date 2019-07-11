---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes 方法
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaecbe3640e5da78c13a077611887c6b62d355a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771511"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="e2ab9-102">ICorDebugSymbolProvider::GetAssemblyImageBytes 方法</span><span class="sxs-lookup"><span data-stu-id="e2ab9-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="e2ab9-103">如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ab9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2ab9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2ab9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2ab9-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="e2ab9-106">[in] 合併組件中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="e2ab9-107">要從合併組件讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="e2ab9-108">位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件，其中包含具有合併組件中繼資料的記憶體緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2ab9-109">備註</span><span class="sxs-lookup"><span data-stu-id="e2ab9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2ab9-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ab9-111">需求</span><span class="sxs-lookup"><span data-stu-id="e2ab9-111">Requirements</span></span>  
 <span data-ttu-id="e2ab9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ab9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ab9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2ab9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2ab9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2ab9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2ab9-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ab9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ab9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ab9-116">See also</span></span>

- [<span data-ttu-id="e2ab9-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="e2ab9-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e2ab9-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e2ab9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
