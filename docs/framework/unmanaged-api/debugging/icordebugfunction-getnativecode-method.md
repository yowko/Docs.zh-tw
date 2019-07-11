---
title: ICorDebugFunction::GetNativeCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0507d59011f6b584ecb1ae11c35c456c80793af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754593"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="ef237-102">ICorDebugFunction::GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="ef237-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="ef237-103">取得這個 ICorDebugFunction 執行個體所表示之函式中的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef237-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef237-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef237-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef237-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef237-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="ef237-106">[out]代表原生程式碼，此函式，或 null，如果此函式是 Microsoft intermediate language (MSIL) 程式碼尚未在 just-in-time (JIT) 編譯 ICorDebugCode 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="ef237-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef237-107">備註</span><span class="sxs-lookup"><span data-stu-id="ef237-107">Remarks</span></span>  
 <span data-ttu-id="ef237-108">如果這由函式`ICorDebugFunction`執行個體已經 JIT 編譯一次以上，如果是泛型型別，`GetNativeCode`傳回隨機的原生程式碼的物件。</span><span class="sxs-lookup"><span data-stu-id="ef237-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef237-109">需求</span><span class="sxs-lookup"><span data-stu-id="ef237-109">Requirements</span></span>  
 <span data-ttu-id="ef237-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef237-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef237-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef237-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef237-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef237-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef237-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef237-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
