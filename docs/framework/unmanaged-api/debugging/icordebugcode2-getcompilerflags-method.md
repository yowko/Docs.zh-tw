---
title: ICorDebugCode2::GetCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4733d59eb14f736f1369de82a7e9c677a65c3f86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093640"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="cd7cf-102">ICorDebugCode2::GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="cd7cf-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="cd7cf-103">取得指定所在這個程式碼物件是其中一個在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 所產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="cd7cf-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd7cf-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd7cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd7cf-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="cd7cf-106">[out]值的指標[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定 JIT 編譯器或原生映像產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="cd7cf-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd7cf-107">需求</span><span class="sxs-lookup"><span data-stu-id="cd7cf-107">Requirements</span></span>  
 <span data-ttu-id="cd7cf-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd7cf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7cf-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd7cf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd7cf-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd7cf-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cd7cf-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cd7cf-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd7cf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd7cf-112">See also</span></span>
