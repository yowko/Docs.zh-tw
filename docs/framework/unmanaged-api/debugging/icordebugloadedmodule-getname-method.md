---
title: ICorDebugLoadedModule::GetName 方法
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bfdf8e43258d14e7298119ce4d7136ea5de54c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415037"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="13fe0-102">ICorDebugLoadedModule::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="13fe0-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="13fe0-103">取得載入模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="13fe0-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13fe0-104">語法</span><span class="sxs-lookup"><span data-stu-id="13fe0-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13fe0-105">參數</span><span class="sxs-lookup"><span data-stu-id="13fe0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="13fe0-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="13fe0-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="13fe0-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="13fe0-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="13fe0-108">[out] 包含載入模組名稱的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="13fe0-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13fe0-109">備註</span><span class="sxs-lookup"><span data-stu-id="13fe0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13fe0-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="13fe0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13fe0-111">需求</span><span class="sxs-lookup"><span data-stu-id="13fe0-111">Requirements</span></span>  
 <span data-ttu-id="13fe0-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13fe0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13fe0-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13fe0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13fe0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13fe0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13fe0-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13fe0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13fe0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13fe0-116">See Also</span></span>  
 [<span data-ttu-id="13fe0-117">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="13fe0-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="13fe0-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="13fe0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
