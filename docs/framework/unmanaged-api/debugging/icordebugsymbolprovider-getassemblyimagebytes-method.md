---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes 方法
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178483"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="3b95c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes 方法</span><span class="sxs-lookup"><span data-stu-id="3b95c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="3b95c-103">如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。</span><span class="sxs-lookup"><span data-stu-id="3b95c-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b95c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b95c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b95c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b95c-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="3b95c-106">[in] 合併組件中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="3b95c-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="3b95c-107">要從合併組件讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="3b95c-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="3b95c-108">指向[ICorDebug記憶緩衝區](icordebugmemorybuffer-interface.md)物件的位址的指標，該物件包含有關具有合併組件中繼資料的記憶體緩衝區的資訊。</span><span class="sxs-lookup"><span data-stu-id="3b95c-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b95c-109">備註</span><span class="sxs-lookup"><span data-stu-id="3b95c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b95c-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3b95c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b95c-111">需求</span><span class="sxs-lookup"><span data-stu-id="3b95c-111">Requirements</span></span>  
 <span data-ttu-id="3b95c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b95c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b95c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b95c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b95c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b95c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b95c-115">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b95c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b95c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b95c-116">See also</span></span>

- [<span data-ttu-id="3b95c-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="3b95c-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="3b95c-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3b95c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
