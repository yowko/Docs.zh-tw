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
ms.openlocfilehash: fb9b5ee329b41a8b842b94d59bd61c8bcf5f0bf5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895141"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="8ab95-102">ICorDebugAppDomain2::GetFunctionPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="8ab95-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="8ab95-103">取得具有指定簽章之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="8ab95-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab95-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ab95-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ab95-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ab95-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="8ab95-106">在函數的類型引數數目。</span><span class="sxs-lookup"><span data-stu-id="8ab95-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="8ab95-107">在指標陣列，其中每一個都會指向代表函式之類型引數的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="8ab95-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="8ab95-108">第一個元素是傳回型別;每個其他元素都是參數類型。</span><span class="sxs-lookup"><span data-stu-id="8ab95-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="8ab95-109">脫銷物件位址的指標，表示函`ICorDebugType`式的指標。</span><span class="sxs-lookup"><span data-stu-id="8ab95-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ab95-110">需求</span><span class="sxs-lookup"><span data-stu-id="8ab95-110">Requirements</span></span>  
 <span data-ttu-id="8ab95-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab95-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ab95-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ab95-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ab95-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ab95-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ab95-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ab95-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
