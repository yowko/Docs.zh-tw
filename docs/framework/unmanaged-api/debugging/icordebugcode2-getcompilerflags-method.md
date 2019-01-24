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
ms.openlocfilehash: df7ecd7403c915df89fe26a0ce9229b88691d19c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667462"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="b46f0-102">ICorDebugCode2::GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="b46f0-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="b46f0-103">取得指定所在這個程式碼物件是其中一個在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 所產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="b46f0-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b46f0-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b46f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="b46f0-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="b46f0-106">[out]值的指標[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定 JIT 編譯器或原生映像產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="b46f0-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46f0-107">需求</span><span class="sxs-lookup"><span data-stu-id="b46f0-107">Requirements</span></span>  
 <span data-ttu-id="b46f0-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b46f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46f0-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b46f0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b46f0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b46f0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b46f0-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46f0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b46f0-112">See also</span></span>

