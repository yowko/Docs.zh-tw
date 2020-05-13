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
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213266"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="7711f-102">ICorDebugFunction::GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="7711f-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="7711f-103">取得此 ICorDebugFunction 實例所表示之函式的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="7711f-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7711f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7711f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7711f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7711f-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7711f-106">脫銷ICorDebugCode 實例的指標，表示此函式的機器碼，如果此函式是不是一次性（JIT）編譯的 Microsoft 中繼語言（MSIL）程式碼，則為 null。</span><span class="sxs-lookup"><span data-stu-id="7711f-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7711f-107">備註</span><span class="sxs-lookup"><span data-stu-id="7711f-107">Remarks</span></span>  
 <span data-ttu-id="7711f-108">如果這個實例所表示的函 `ICorDebugFunction` 式已多次進行 JIT 編譯，則在泛型型別的情況下，會傳回 `GetNativeCode` 隨機機器碼物件。</span><span class="sxs-lookup"><span data-stu-id="7711f-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7711f-109">需求</span><span class="sxs-lookup"><span data-stu-id="7711f-109">Requirements</span></span>  
 <span data-ttu-id="7711f-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7711f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7711f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7711f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7711f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7711f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7711f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7711f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
