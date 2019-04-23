---
title: ICorDebugLoadedModule::GetName 方法
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111263"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="815a5-102">ICorDebugLoadedModule::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="815a5-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="815a5-103">取得載入模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="815a5-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="815a5-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="815a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="815a5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="815a5-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="815a5-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="815a5-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="815a5-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="815a5-108">[out] 包含載入模組名稱的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="815a5-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="815a5-109">備註</span><span class="sxs-lookup"><span data-stu-id="815a5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="815a5-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="815a5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815a5-111">需求</span><span class="sxs-lookup"><span data-stu-id="815a5-111">Requirements</span></span>  
 <span data-ttu-id="815a5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="815a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815a5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="815a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="815a5-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="815a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815a5-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815a5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815a5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="815a5-116">See also</span></span>

- [<span data-ttu-id="815a5-117">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="815a5-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="815a5-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="815a5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
