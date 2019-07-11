---
title: ICorDebugFunction::GetILCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754676"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="4d12a-102">ICorDebugFunction::GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="4d12a-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="4d12a-103">取得 ICorDebugCode 執行個體，表示與這個 ICorDebugFunction 物件相關聯的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d12a-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d12a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d12a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d12a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d12a-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="4d12a-106">[out]指標`ICorDebugCode`執行個體，則為 null，如果函式不編譯為 MSIL。</span><span class="sxs-lookup"><span data-stu-id="4d12a-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d12a-107">備註</span><span class="sxs-lookup"><span data-stu-id="4d12a-107">Remarks</span></span>  
 <span data-ttu-id="4d12a-108">如果已在此函式，允許編輯後繼續`GetILCode`方法會對應到此函式已編輯版本的 common language runtime (CLR) 中的程式碼的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d12a-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d12a-109">需求</span><span class="sxs-lookup"><span data-stu-id="4d12a-109">Requirements</span></span>  
 <span data-ttu-id="4d12a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d12a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d12a-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d12a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d12a-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d12a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d12a-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d12a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
