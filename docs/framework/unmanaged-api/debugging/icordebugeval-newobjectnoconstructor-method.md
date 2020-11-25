---
title: ICorDebugEval::NewObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: bb27ec755fb83dc71af7dd48b5ed6e7699436335
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729725"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="98f59-102">ICorDebugEval::NewObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="98f59-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="98f59-103">配置指定類型的新物件實例，而不嘗試呼叫函式方法。</span><span class="sxs-lookup"><span data-stu-id="98f59-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="98f59-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="98f59-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="98f59-105">請改用 [ICorDebugEval2：： NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="98f59-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f59-106">語法</span><span class="sxs-lookup"><span data-stu-id="98f59-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98f59-107">參數</span><span class="sxs-lookup"><span data-stu-id="98f59-107">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="98f59-108">在ICorDebugClass 物件的指標，該物件代表要具現化之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="98f59-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98f59-109">需求</span><span class="sxs-lookup"><span data-stu-id="98f59-109">Requirements</span></span>  

 <span data-ttu-id="98f59-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98f59-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98f59-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98f59-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98f59-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98f59-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98f59-113">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="98f59-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f59-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98f59-114">See also</span></span>

- [<span data-ttu-id="98f59-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="98f59-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
