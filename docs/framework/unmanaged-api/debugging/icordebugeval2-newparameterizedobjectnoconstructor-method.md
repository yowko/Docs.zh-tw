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
ms.openlocfilehash: 796c6aa4c42a037fe612b4b1ee5267a678cf5224
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729638"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="b1688-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="b1688-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="b1688-103">將指定類別的新參數化型別物件具現化，而不會嘗試呼叫函式方法。</span><span class="sxs-lookup"><span data-stu-id="b1688-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1688-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1688-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1688-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1688-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="b1688-106">在ICorDebugClass 物件的指標，代表要具現化之物件的類別。</span><span class="sxs-lookup"><span data-stu-id="b1688-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="b1688-107">在傳遞的型別引數數目。</span><span class="sxs-lookup"><span data-stu-id="b1688-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="b1688-108">在指標的陣列，每個指標都會指向 ICorDebugType 物件，該物件代表要具現化之物件的型別引數。</span><span class="sxs-lookup"><span data-stu-id="b1688-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1688-109">備註</span><span class="sxs-lookup"><span data-stu-id="b1688-109">Remarks</span></span>  

 <span data-ttu-id="b1688-110">`NewParameterizedObjectNoConstructor`如果傳遞的類型引數數目不正確或類型引數的類型不正確，此方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="b1688-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1688-111">需求</span><span class="sxs-lookup"><span data-stu-id="b1688-111">Requirements</span></span>  

 <span data-ttu-id="b1688-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1688-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1688-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1688-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1688-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1688-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1688-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1688-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
