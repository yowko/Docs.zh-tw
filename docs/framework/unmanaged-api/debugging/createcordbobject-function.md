---
title: CreateCordbObject 函式
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12898f75d2575e539b018ea367bc870a3dc738a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406327"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="4f7a8-102">CreateCordbObject 函式</span><span class="sxs-lookup"><span data-stu-id="4f7a8-102">CreateCordbObject Function</span></span>
<span data-ttu-id="4f7a8-103">建立偵錯工具介面 ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) 針對受管理的偵錯工作階段，在遠端處理序上具現化提供的功能。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f7a8-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f7a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f7a8-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="4f7a8-106">[in] 目標處理序的偵錯工具版本。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="4f7a8-107">這個參數必須是 CorDebugVersion_2_0，才能進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="4f7a8-108">[out]指標可以轉換成物件的指標[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面，並傳回。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f7a8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4f7a8-109">Return Value</span></span>  
 <span data-ttu-id="4f7a8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f7a8-110">S_OK</span></span>  
 <span data-ttu-id="4f7a8-111">已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="4f7a8-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4f7a8-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="4f7a8-113">`ppCordb` 為 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="4f7a8-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4f7a8-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="4f7a8-115">無法為 `ppCordb` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="4f7a8-116">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="4f7a8-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4f7a8-117">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f7a8-118">備註</span><span class="sxs-lookup"><span data-stu-id="4f7a8-118">Remarks</span></span>  
 <span data-ttu-id="4f7a8-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)中傳回的介面`ppCordb`是所有受管理的偵錯服務的最上層的偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f7a8-120">需求</span><span class="sxs-lookup"><span data-stu-id="4f7a8-120">Requirements</span></span>  
 <span data-ttu-id="4f7a8-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f7a8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f7a8-122">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="4f7a8-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="4f7a8-123">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="4f7a8-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="4f7a8-124">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4f7a8-124">**.NET Framework Versions:** 3.5 SP1</span></span>
