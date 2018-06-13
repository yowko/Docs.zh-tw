---
title: ICorDebugManagedCallback::UnloadAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a892012e872dcf44512adbe0d6890812d84ed899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412590"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="6b793-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6b793-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="6b793-103">告知偵錯工具通用語言執行階段組件已卸載。</span><span class="sxs-lookup"><span data-stu-id="6b793-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b793-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b793-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b793-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b793-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6b793-106">[in]表示包含組件的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="6b793-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="6b793-107">[in]代表組件 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="6b793-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b793-108">備註</span><span class="sxs-lookup"><span data-stu-id="6b793-108">Remarks</span></span>  
 <span data-ttu-id="6b793-109">組件不應該使用這個回呼之後。</span><span class="sxs-lookup"><span data-stu-id="6b793-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b793-110">需求</span><span class="sxs-lookup"><span data-stu-id="6b793-110">Requirements</span></span>  
 <span data-ttu-id="6b793-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b793-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b793-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b793-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b793-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b793-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b793-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b793-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b793-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b793-115">See Also</span></span>  
 [<span data-ttu-id="6b793-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6b793-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="6b793-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6b793-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
