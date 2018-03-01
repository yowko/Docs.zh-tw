---
title: "ICorDebugFunction::GetNativeCode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15383198da740f536061f1568fb06f042117b19c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="1e47d-102">ICorDebugFunction::GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="1e47d-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="1e47d-103">取得原生程式碼的函式，由這個 ICorDebugFunction 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e47d-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e47d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e47d-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e47d-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e47d-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="1e47d-106">[out]ICorDebugCode 執行個體，代表原生程式碼，此函式，或 null，如有此函式是 Microsoft intermediate language (MSIL) 程式碼尚未在 just-in-time (JIT) 編譯的指標。</span><span class="sxs-lookup"><span data-stu-id="1e47d-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e47d-107">備註</span><span class="sxs-lookup"><span data-stu-id="1e47d-107">Remarks</span></span>  
 <span data-ttu-id="1e47d-108">如果這由函式`ICorDebugFunction`執行個體已被 JIT 編譯一次以上，如果是泛型型別，`GetNativeCode`傳回隨機的原生程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="1e47d-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e47d-109">需求</span><span class="sxs-lookup"><span data-stu-id="1e47d-109">Requirements</span></span>  
 <span data-ttu-id="1e47d-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e47d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e47d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e47d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e47d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e47d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e47d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e47d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
