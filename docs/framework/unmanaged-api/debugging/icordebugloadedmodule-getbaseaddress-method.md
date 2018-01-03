---
title: "ICorDebugLoadedModule::GetBaseAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d71b1db35a9e2747e7e14787f385f42f98305c61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="46199-102">ICorDebugLoadedModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="46199-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="46199-103">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="46199-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46199-104">語法</span><span class="sxs-lookup"><span data-stu-id="46199-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46199-105">參數</span><span class="sxs-lookup"><span data-stu-id="46199-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="46199-106">[out] 載入模組的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="46199-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46199-107">備註</span><span class="sxs-lookup"><span data-stu-id="46199-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46199-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="46199-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46199-109">需求</span><span class="sxs-lookup"><span data-stu-id="46199-109">Requirements</span></span>  
 <span data-ttu-id="46199-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46199-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46199-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46199-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46199-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46199-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46199-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46199-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46199-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="46199-114">See Also</span></span>  
 [<span data-ttu-id="46199-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="46199-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="46199-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="46199-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
