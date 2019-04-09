---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183465"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="70cec-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="70cec-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="70cec-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="70cec-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cec-104">語法</span><span class="sxs-lookup"><span data-stu-id="70cec-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70cec-105">參數</span><span class="sxs-lookup"><span data-stu-id="70cec-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="70cec-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="70cec-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70cec-107">備註</span><span class="sxs-lookup"><span data-stu-id="70cec-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70cec-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="70cec-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cec-109">需求</span><span class="sxs-lookup"><span data-stu-id="70cec-109">Requirements</span></span>  
 <span data-ttu-id="70cec-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70cec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cec-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70cec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70cec-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70cec-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70cec-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="70cec-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70cec-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70cec-114">See also</span></span>

- [<span data-ttu-id="70cec-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="70cec-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="70cec-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70cec-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
