---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 2d5b07acb9dc374fdd8872ed982a92171da28603
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137225"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="3efe4-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="3efe4-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="3efe4-103">取得目前的編譯器旗標設定，common language runtime （CLR）用來選取要載入此進程的正確先行編譯（也就是原生）影像。</span><span class="sxs-lookup"><span data-stu-id="3efe4-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3efe4-104">語法</span><span class="sxs-lookup"><span data-stu-id="3efe4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3efe4-105">參數</span><span class="sxs-lookup"><span data-stu-id="3efe4-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="3efe4-106">脫銷[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值的位元組合指標，用來選取要載入的正確先行編譯映射。</span><span class="sxs-lookup"><span data-stu-id="3efe4-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3efe4-107">備註</span><span class="sxs-lookup"><span data-stu-id="3efe4-107">Remarks</span></span>  
 <span data-ttu-id="3efe4-108">請使用[ICorDebugProcess2：： SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)方法來設定旗標，以供 CLR 用來選取要載入的正確預先編譯影像。</span><span class="sxs-lookup"><span data-stu-id="3efe4-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3efe4-109">需求</span><span class="sxs-lookup"><span data-stu-id="3efe4-109">Requirements</span></span>  
 <span data-ttu-id="3efe4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3efe4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3efe4-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3efe4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3efe4-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3efe4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3efe4-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3efe4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
