---
title: ICorDebugLoadedModule::GetSize 方法
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c4888419bb13db43a4a15d98965cc8d3cb8e77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515571"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="49733-102">ICorDebugLoadedModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="49733-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="49733-103">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="49733-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49733-104">語法</span><span class="sxs-lookup"><span data-stu-id="49733-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49733-105">參數</span><span class="sxs-lookup"><span data-stu-id="49733-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="49733-106">[out] 載入模組中之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="49733-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49733-107">備註</span><span class="sxs-lookup"><span data-stu-id="49733-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49733-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="49733-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49733-109">需求</span><span class="sxs-lookup"><span data-stu-id="49733-109">Requirements</span></span>  
 <span data-ttu-id="49733-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49733-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49733-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49733-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49733-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49733-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49733-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49733-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49733-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49733-114">See also</span></span>
- [<span data-ttu-id="49733-115">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="49733-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="49733-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="49733-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
