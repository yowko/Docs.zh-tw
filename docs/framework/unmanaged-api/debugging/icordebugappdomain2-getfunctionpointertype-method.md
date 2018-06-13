---
title: ICorDebugAppDomain2::GetFunctionPointerType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d497fd8e659a24add25df63c4ce48e710dcb0c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403789"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="3152c-102">ICorDebugAppDomain2::GetFunctionPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="3152c-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="3152c-103">取得具有指定簽章的函式指標。</span><span class="sxs-lookup"><span data-stu-id="3152c-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3152c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3152c-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3152c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3152c-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="3152c-106">[in]此函式的型別引數數目。</span><span class="sxs-lookup"><span data-stu-id="3152c-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="3152c-107">[in]指標的陣列，其中每個指向 ICorDebugType 物件，表示型別引數的函式。</span><span class="sxs-lookup"><span data-stu-id="3152c-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="3152c-108">第一個項目是傳回的型別。每個其他項目是參數型別。</span><span class="sxs-lookup"><span data-stu-id="3152c-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="3152c-109">[out]位址指標`ICorDebugType`物件，表示函式的指標。</span><span class="sxs-lookup"><span data-stu-id="3152c-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3152c-110">需求</span><span class="sxs-lookup"><span data-stu-id="3152c-110">Requirements</span></span>  
 <span data-ttu-id="3152c-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3152c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3152c-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3152c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3152c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3152c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3152c-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3152c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
