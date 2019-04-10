---
title: ICorDebugLoadedModule::GetBaseAddress 方法
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e84d6deca0cd09cc547636007208c70ab91c1ab1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223533"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="6cb94-102">ICorDebugLoadedModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="6cb94-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="6cb94-103">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="6cb94-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb94-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cb94-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cb94-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cb94-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6cb94-106">[out] 載入模組的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="6cb94-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cb94-107">備註</span><span class="sxs-lookup"><span data-stu-id="6cb94-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cb94-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6cb94-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb94-109">需求</span><span class="sxs-lookup"><span data-stu-id="6cb94-109">Requirements</span></span>  
 <span data-ttu-id="6cb94-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cb94-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb94-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cb94-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cb94-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cb94-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6cb94-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6cb94-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb94-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cb94-114">See also</span></span>

- [<span data-ttu-id="6cb94-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="6cb94-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="6cb94-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6cb94-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
