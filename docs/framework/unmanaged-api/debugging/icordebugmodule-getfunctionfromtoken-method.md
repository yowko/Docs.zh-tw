---
title: ICorDebugModule::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: cb966a918c63b4fbc00dcf52819b9384427dfdaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129593"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="aef83-102">ICorDebugModule::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="aef83-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="aef83-103">取得元資料標記所指定的函式。</span><span class="sxs-lookup"><span data-stu-id="aef83-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef83-104">語法</span><span class="sxs-lookup"><span data-stu-id="aef83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef83-105">參數</span><span class="sxs-lookup"><span data-stu-id="aef83-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="aef83-106">在參考函數中繼資料的 `mdMethodDef` 中繼資料 token。</span><span class="sxs-lookup"><span data-stu-id="aef83-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="aef83-107">脫銷代表函式之 ICorDebugFunction 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="aef83-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aef83-108">備註</span><span class="sxs-lookup"><span data-stu-id="aef83-108">Remarks</span></span>  
 <span data-ttu-id="aef83-109">如果傳入的值 `methodDef` 未參考 Microsoft 中繼語言（MSIL）方法，`GetFunctionFromToken` 方法就會傳回 CORDBG_E_FUNCTION_NOT_IL HRESULT。</span><span class="sxs-lookup"><span data-stu-id="aef83-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef83-110">需求</span><span class="sxs-lookup"><span data-stu-id="aef83-110">Requirements</span></span>  
 <span data-ttu-id="aef83-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aef83-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef83-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aef83-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aef83-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef83-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aef83-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
