---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936867"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="71b83-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="71b83-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="71b83-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="71b83-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="71b83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71b83-105">參數</span><span class="sxs-lookup"><span data-stu-id="71b83-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="71b83-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="71b83-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71b83-107">備註</span><span class="sxs-lookup"><span data-stu-id="71b83-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71b83-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="71b83-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71b83-109">需求</span><span class="sxs-lookup"><span data-stu-id="71b83-109">Requirements</span></span>  
 <span data-ttu-id="71b83-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71b83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71b83-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71b83-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71b83-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71b83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71b83-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71b83-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b83-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b83-114">See also</span></span>

- [<span data-ttu-id="71b83-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="71b83-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="71b83-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="71b83-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
