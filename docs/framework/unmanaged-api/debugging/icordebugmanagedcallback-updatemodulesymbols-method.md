---
title: "ICorDebugManagedCallback::UpdateModuleSymbols 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UpdateModuleSymbols
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a1606c256bbfd3b0a7de29b84aace1b4831a016
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="87cae-102">ICorDebugManagedCallback::UpdateModuleSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="87cae-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="87cae-103">告知偵錯工具通用語言執行階段模組的符號，已變更。</span><span class="sxs-lookup"><span data-stu-id="87cae-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87cae-104">語法</span><span class="sxs-lookup"><span data-stu-id="87cae-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87cae-105">參數</span><span class="sxs-lookup"><span data-stu-id="87cae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="87cae-106">[in]表示模組符號已經變更的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="87cae-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="87cae-107">[in]ICorDebugModule 物件，表示的模組符號已經變更指標。</span><span class="sxs-lookup"><span data-stu-id="87cae-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="87cae-108">[in]Win32 COM 指標`IStream`物件，其中包含已修改的符號。</span><span class="sxs-lookup"><span data-stu-id="87cae-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87cae-109">備註</span><span class="sxs-lookup"><span data-stu-id="87cae-109">Remarks</span></span>  
 <span data-ttu-id="87cae-110">這個方法會提供機會更新模組的符號偵錯工具的檢視，藉由呼叫[isymunmanagedreader:: Updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)或[isymunmanagedreader:: Replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)。</span><span class="sxs-lookup"><span data-stu-id="87cae-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="87cae-111">這個回呼可能會多次發生相同的模組。</span><span class="sxs-lookup"><span data-stu-id="87cae-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="87cae-112">偵錯工具應該嘗試繫結未繫結的來源層級中斷點。</span><span class="sxs-lookup"><span data-stu-id="87cae-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87cae-113">需求</span><span class="sxs-lookup"><span data-stu-id="87cae-113">Requirements</span></span>  
 <span data-ttu-id="87cae-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87cae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87cae-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87cae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87cae-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87cae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87cae-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87cae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cae-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87cae-118">See Also</span></span>  
 [<span data-ttu-id="87cae-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="87cae-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
