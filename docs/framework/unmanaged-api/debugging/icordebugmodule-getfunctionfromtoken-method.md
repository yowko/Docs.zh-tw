---
title: "ICorDebugModule::GetFunctionFromToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetFunctionFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c449b49333de562cd5ed07f827da6bc295e9c3c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="ce0e4-102">ICorDebugModule::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="ce0e4-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="ce0e4-103">取得指定中繼資料語彙基元的函式。</span><span class="sxs-lookup"><span data-stu-id="ce0e4-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce0e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce0e4-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce0e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce0e4-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="ce0e4-106">[in]A`mdMethodDef`參考函式的中繼資料的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ce0e4-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="ce0e4-107">[out]ICorDebugFunction 介面物件，表示函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="ce0e4-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce0e4-108">備註</span><span class="sxs-lookup"><span data-stu-id="ce0e4-108">Remarks</span></span>  
 <span data-ttu-id="ce0e4-109">`GetFunctionFromToken`如果傳入的值，方法會傳回 CORDBG_E_FUNCTION_NOT_IL HRESULT`methodDef`未參考 Microsoft intermediate language (MSIL) 方法。</span><span class="sxs-lookup"><span data-stu-id="ce0e4-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce0e4-110">需求</span><span class="sxs-lookup"><span data-stu-id="ce0e4-110">Requirements</span></span>  
 <span data-ttu-id="ce0e4-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce0e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce0e4-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce0e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce0e4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce0e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce0e4-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce0e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
