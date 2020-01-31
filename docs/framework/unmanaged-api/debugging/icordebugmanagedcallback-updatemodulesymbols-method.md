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
ms.openlocfilehash: 2b64122489481c6b0fde605015720d0a56ba8fe2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788316"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="bcf90-102">ICorDebugManagedCallback::UpdateModuleSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="bcf90-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="bcf90-103">通知偵錯工具，通用語言執行時間模組的符號已經變更。</span><span class="sxs-lookup"><span data-stu-id="bcf90-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf90-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcf90-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcf90-105">參數</span><span class="sxs-lookup"><span data-stu-id="bcf90-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bcf90-106">在ICorDebugAppDomain 物件的指標，代表包含已變更符號之模組的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="bcf90-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="bcf90-107">在ICorDebugModule 物件的指標，表示符號已變更的模組。</span><span class="sxs-lookup"><span data-stu-id="bcf90-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="bcf90-108">在Win32 COM `IStream` 物件的指標，其中包含修改過的符號。</span><span class="sxs-lookup"><span data-stu-id="bcf90-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcf90-109">備註</span><span class="sxs-lookup"><span data-stu-id="bcf90-109">Remarks</span></span>  
 <span data-ttu-id="bcf90-110">這個方法可讓您藉由呼叫[ISymUnmanagedReader：： UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)或[ISymUnmanagedReader：： ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)，來更新偵錯工具的模組符號的觀點。</span><span class="sxs-lookup"><span data-stu-id="bcf90-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="bcf90-111">針對相同的模組，此回呼可能會發生多次。</span><span class="sxs-lookup"><span data-stu-id="bcf90-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="bcf90-112">偵錯工具應該嘗試系結未系結的來源層級中斷點。</span><span class="sxs-lookup"><span data-stu-id="bcf90-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf90-113">需求</span><span class="sxs-lookup"><span data-stu-id="bcf90-113">Requirements</span></span>  
 <span data-ttu-id="bcf90-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcf90-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf90-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcf90-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcf90-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcf90-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcf90-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf90-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf90-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcf90-118">See also</span></span>

- [<span data-ttu-id="bcf90-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bcf90-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
