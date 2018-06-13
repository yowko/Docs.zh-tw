---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413227"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="76128-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="76128-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="76128-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="76128-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76128-104">語法</span><span class="sxs-lookup"><span data-stu-id="76128-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76128-105">參數</span><span class="sxs-lookup"><span data-stu-id="76128-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="76128-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="76128-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76128-107">備註</span><span class="sxs-lookup"><span data-stu-id="76128-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76128-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="76128-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76128-109">需求</span><span class="sxs-lookup"><span data-stu-id="76128-109">Requirements</span></span>  
 <span data-ttu-id="76128-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76128-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76128-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76128-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76128-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76128-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76128-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76128-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76128-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76128-114">See Also</span></span>  
 [<span data-ttu-id="76128-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="76128-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="76128-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="76128-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
