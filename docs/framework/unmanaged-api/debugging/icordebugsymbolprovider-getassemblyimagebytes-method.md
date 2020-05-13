---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes 方法
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376122"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="8e282-102">ICorDebugSymbolProvider::GetAssemblyImageBytes 方法</span><span class="sxs-lookup"><span data-stu-id="8e282-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="8e282-103">如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。</span><span class="sxs-lookup"><span data-stu-id="8e282-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e282-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e282-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e282-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e282-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="8e282-106">[in] 合併組件中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="8e282-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="8e282-107">要從合併組件讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8e282-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="8e282-108">[ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)物件位址的指標，其中包含具有合併元件中繼資料之記憶體緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8e282-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e282-109">備註</span><span class="sxs-lookup"><span data-stu-id="8e282-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e282-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8e282-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e282-111">需求</span><span class="sxs-lookup"><span data-stu-id="8e282-111">Requirements</span></span>  
 <span data-ttu-id="8e282-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e282-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e282-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e282-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e282-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e282-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e282-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e282-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e282-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e282-116">See also</span></span>

- [<span data-ttu-id="8e282-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8e282-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8e282-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8e282-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
