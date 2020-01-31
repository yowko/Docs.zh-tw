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
ms.openlocfilehash: 4ad1fb1bcb43dda9796b54cbf868f89c001995da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777896"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="4f33c-102">ICorDebugCode2::GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="4f33c-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="4f33c-103">取得指定條件的旗標，此程式碼物件是使用原生映射產生器（Ngen.exe）編譯或產生的即時（JIT）。</span><span class="sxs-lookup"><span data-stu-id="4f33c-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="4f33c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f33c-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="4f33c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f33c-105">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="4f33c-106">脫銷[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的指標，指定 JIT 編譯程式或原生映射產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="4f33c-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f33c-107">需求</span><span class="sxs-lookup"><span data-stu-id="4f33c-107">Requirements</span></span>

<span data-ttu-id="4f33c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f33c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="4f33c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f33c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="4f33c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f33c-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="4f33c-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f33c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
