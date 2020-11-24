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
ms.openlocfilehash: 223f66639ae24f2a54f1bc936f4a0765573356eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673887"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="6cc21-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="6cc21-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="6cc21-103">取得 common language runtime (CLR) 用來選取正確先行編譯 (的目前編譯器旗標設定，也就是要載入此進程中的原生) 映射。</span><span class="sxs-lookup"><span data-stu-id="6cc21-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc21-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cc21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cc21-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cc21-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="6cc21-106">擴展 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉值的位元組合指標，用來選取要載入的正確先行編譯映射。</span><span class="sxs-lookup"><span data-stu-id="6cc21-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cc21-107">備註</span><span class="sxs-lookup"><span data-stu-id="6cc21-107">Remarks</span></span>  

 <span data-ttu-id="6cc21-108">您可以使用 [ICorDebugProcess2：： SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) 方法，設定 CLR 將用來選取要載入之正確預先編譯映射的旗標。</span><span class="sxs-lookup"><span data-stu-id="6cc21-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cc21-109">需求</span><span class="sxs-lookup"><span data-stu-id="6cc21-109">Requirements</span></span>  

 <span data-ttu-id="6cc21-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cc21-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cc21-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cc21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cc21-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cc21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cc21-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cc21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
