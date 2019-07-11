---
title: ICorDebugModule2::GetJITCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88277be93d3a0e445e97217655d3d524962dd01d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764229"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="b05d2-102">ICorDebugModule2::GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="b05d2-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="b05d2-103">取得控制此 ICorDebugModule2-just-in-time (JIT) 編譯的旗標。</span><span class="sxs-lookup"><span data-stu-id="b05d2-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b05d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="b05d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b05d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="b05d2-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="b05d2-106">[out]值的指標[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，用於控制 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="b05d2-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b05d2-107">需求</span><span class="sxs-lookup"><span data-stu-id="b05d2-107">Requirements</span></span>  
 <span data-ttu-id="b05d2-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b05d2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b05d2-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b05d2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b05d2-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b05d2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b05d2-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b05d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
