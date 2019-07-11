---
title: ICorDebugManagedCallback::UpdateModuleSymbols 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a15e3ab0d50763ad53b1caa921035239868fec1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761240"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="7e075-102">ICorDebugManagedCallback::UpdateModuleSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="7e075-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="7e075-103">已變更為通用語言執行階段模組的符號會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7e075-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e075-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e075-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e075-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e075-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7e075-106">[in]表示包含的模組的符號已經變更的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="7e075-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="7e075-107">[in]ICorDebugModule 物件，表示的模組符號已經變更指標。</span><span class="sxs-lookup"><span data-stu-id="7e075-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="7e075-108">[in]Win32 COM 指標`IStream`物件，其中包含已修改的符號。</span><span class="sxs-lookup"><span data-stu-id="7e075-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e075-109">備註</span><span class="sxs-lookup"><span data-stu-id="7e075-109">Remarks</span></span>  
 <span data-ttu-id="7e075-110">這個方法便有機會呼叫來更新模組的符號偵錯工具的檢視[isymunmanagedreader:: Updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)或是[isymunmanagedreader:: Replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7e075-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="7e075-111">此回呼可能會多次發生相同的模組。</span><span class="sxs-lookup"><span data-stu-id="7e075-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="7e075-112">偵錯工具應該嘗試繫結未繫結的來源層級中斷點。</span><span class="sxs-lookup"><span data-stu-id="7e075-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e075-113">需求</span><span class="sxs-lookup"><span data-stu-id="7e075-113">Requirements</span></span>  
 <span data-ttu-id="7e075-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e075-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e075-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e075-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e075-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e075-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e075-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e075-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e075-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e075-118">See also</span></span>

- [<span data-ttu-id="7e075-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7e075-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
