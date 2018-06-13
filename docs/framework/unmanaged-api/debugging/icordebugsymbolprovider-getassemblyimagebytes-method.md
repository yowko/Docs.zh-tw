---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes 方法
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7975ca3da16be10285e618752981249602371c43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418587"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="3957f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes 方法</span><span class="sxs-lookup"><span data-stu-id="3957f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="3957f-103">如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。</span><span class="sxs-lookup"><span data-stu-id="3957f-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3957f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3957f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3957f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3957f-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="3957f-106">[in] 合併組件中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="3957f-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="3957f-107">要從合併組件讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="3957f-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="3957f-108">位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件，其中包含具有合併組件中繼資料之記憶體緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3957f-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3957f-109">備註</span><span class="sxs-lookup"><span data-stu-id="3957f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3957f-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="3957f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3957f-111">需求</span><span class="sxs-lookup"><span data-stu-id="3957f-111">Requirements</span></span>  
 <span data-ttu-id="3957f-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3957f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3957f-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3957f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3957f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3957f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3957f-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3957f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3957f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3957f-116">See Also</span></span>  
 [<span data-ttu-id="3957f-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="3957f-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3957f-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3957f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
