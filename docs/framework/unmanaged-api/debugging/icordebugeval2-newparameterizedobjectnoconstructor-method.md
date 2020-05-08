---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 90fce1710f97341fb49be1d07f7af2edf8cb848c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976079"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="f44e8-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="f44e8-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="f44e8-103">將指定類別的新參數化型別物件具現化，而不嘗試呼叫函式方法。</span><span class="sxs-lookup"><span data-stu-id="f44e8-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f44e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="f44e8-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f44e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="f44e8-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f44e8-106">在ICorDebugClass 物件的指標，表示要具現化之物件的類別。</span><span class="sxs-lookup"><span data-stu-id="f44e8-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f44e8-107">在傳遞的型別引數數目。</span><span class="sxs-lookup"><span data-stu-id="f44e8-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f44e8-108">在指標的陣列，其中每一個都會指向 ICorDebugType 物件，代表正在具現化之物件的型別引數。</span><span class="sxs-lookup"><span data-stu-id="f44e8-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f44e8-109">備註</span><span class="sxs-lookup"><span data-stu-id="f44e8-109">Remarks</span></span>  
 <span data-ttu-id="f44e8-110">如果`NewParameterizedObjectNoConstructor`傳遞的類型引數數目不正確或類型引數的類型錯誤，此方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f44e8-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f44e8-111">需求</span><span class="sxs-lookup"><span data-stu-id="f44e8-111">Requirements</span></span>  
 <span data-ttu-id="f44e8-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f44e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f44e8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f44e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f44e8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f44e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f44e8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f44e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
