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
ms.openlocfilehash: ab6551ba70ed4cd154b166eeb92138b6550d2cb2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792970"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="dbe48-102">ICorDebugModule2::GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="dbe48-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="dbe48-103">取得旗標，控制這個 ICorDebugModule2 的即時（JIT）編譯。</span><span class="sxs-lookup"><span data-stu-id="dbe48-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe48-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbe48-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbe48-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbe48-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="dbe48-106">脫銷控制 JIT 編譯之[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="dbe48-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe48-107">需求</span><span class="sxs-lookup"><span data-stu-id="dbe48-107">Requirements</span></span>  
 <span data-ttu-id="dbe48-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe48-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe48-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbe48-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbe48-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbe48-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbe48-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe48-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
