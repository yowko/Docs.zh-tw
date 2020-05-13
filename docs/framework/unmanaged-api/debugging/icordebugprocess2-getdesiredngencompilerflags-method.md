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
ms.openlocfilehash: d2e54f0b16300673409eb2f5757338dfa3011e61
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212993"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="42f59-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="42f59-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="42f59-103">取得目前的編譯器旗標設定，common language runtime （CLR）用來選取要載入此進程的正確先行編譯（也就是原生）影像。</span><span class="sxs-lookup"><span data-stu-id="42f59-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f59-104">語法</span><span class="sxs-lookup"><span data-stu-id="42f59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42f59-105">參數</span><span class="sxs-lookup"><span data-stu-id="42f59-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="42f59-106">脫銷[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的位元組合指標，用來選取要載入的正確先行編譯映射。</span><span class="sxs-lookup"><span data-stu-id="42f59-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42f59-107">備註</span><span class="sxs-lookup"><span data-stu-id="42f59-107">Remarks</span></span>  
 <span data-ttu-id="42f59-108">請使用[ICorDebugProcess2：： SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md)方法來設定旗標，以供 CLR 用來選取要載入的正確預先編譯影像。</span><span class="sxs-lookup"><span data-stu-id="42f59-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42f59-109">需求</span><span class="sxs-lookup"><span data-stu-id="42f59-109">Requirements</span></span>  
 <span data-ttu-id="42f59-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42f59-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f59-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42f59-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42f59-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42f59-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42f59-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f59-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
