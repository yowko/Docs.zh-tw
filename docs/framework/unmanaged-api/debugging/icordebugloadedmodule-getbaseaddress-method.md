---
title: ICorDebugLoadedModule::GetBaseAddress 方法
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5ef73be22ea79d15ec53e8ab33c34441002acce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732423"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f5146-102">ICorDebugLoadedModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="f5146-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f5146-103">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="f5146-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5146-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5146-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5146-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5146-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f5146-106">[out] 載入模組的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="f5146-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5146-107">備註</span><span class="sxs-lookup"><span data-stu-id="f5146-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5146-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="f5146-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5146-109">需求</span><span class="sxs-lookup"><span data-stu-id="f5146-109">Requirements</span></span>  
 <span data-ttu-id="f5146-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5146-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5146-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5146-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5146-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5146-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5146-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5146-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5146-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5146-114">See also</span></span>
- [<span data-ttu-id="f5146-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="f5146-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f5146-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f5146-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
