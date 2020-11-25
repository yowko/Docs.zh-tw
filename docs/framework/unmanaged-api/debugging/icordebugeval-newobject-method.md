---
title: ICorDebugEval::NewObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: a4d6dd0df9f38561ab5014d7ab65fde6793c9846
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729742"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="5b298-102">ICorDebugEval::NewObject 方法</span><span class="sxs-lookup"><span data-stu-id="5b298-102">ICorDebugEval::NewObject Method</span></span>

<span data-ttu-id="5b298-103">配置新的物件實例，並呼叫指定的函式方法。</span><span class="sxs-lookup"><span data-stu-id="5b298-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="5b298-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="5b298-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5b298-105">請改用 [ICorDebugEval2：： NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="5b298-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b298-106">語法</span><span class="sxs-lookup"><span data-stu-id="5b298-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b298-107">參數</span><span class="sxs-lookup"><span data-stu-id="5b298-107">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="5b298-108">在要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="5b298-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="5b298-109">[in] `ppArgs` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5b298-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="5b298-110">在ICorDebugValue 物件的陣列，每個物件都代表要傳遞給函式的引數。</span><span class="sxs-lookup"><span data-stu-id="5b298-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b298-111">需求</span><span class="sxs-lookup"><span data-stu-id="5b298-111">Requirements</span></span>  

 <span data-ttu-id="5b298-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b298-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b298-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b298-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b298-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b298-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b298-115">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="5b298-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b298-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b298-116">See also</span></span>

- [<span data-ttu-id="5b298-117">NewParameterizedObject 方法</span><span class="sxs-lookup"><span data-stu-id="5b298-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
