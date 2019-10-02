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
ms.openlocfilehash: 1605ee92c8743606ff0e958f112a2d90af43e03a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700721"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="fef37-102">ICorDebugCode2::GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="fef37-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="fef37-103">取得指定條件的旗標，此程式碼物件是使用原生映射產生器（Ngen.exe）編譯或產生的即時（JIT）。</span><span class="sxs-lookup"><span data-stu-id="fef37-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="fef37-104">語法</span><span class="sxs-lookup"><span data-stu-id="fef37-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="fef37-105">參數</span><span class="sxs-lookup"><span data-stu-id="fef37-105">Parameters</span></span>

 `pdwFlags`  
 <span data-ttu-id="fef37-106">脫銷[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值的指標，指定 JIT 編譯程式或原生映射產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="fef37-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="fef37-107">需求</span><span class="sxs-lookup"><span data-stu-id="fef37-107">Requirements</span></span>

 <span data-ttu-id="fef37-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fef37-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="fef37-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fef37-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="fef37-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fef37-110">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="fef37-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef37-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
