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
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213617"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="55186-102">ICorDebugFunction::GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="55186-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="55186-103">取得 ICorDebugCode 實例，代表與這個 ICorDebugFunction 物件相關聯的 Microsoft 中繼語言（MSIL）程式碼。</span><span class="sxs-lookup"><span data-stu-id="55186-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55186-104">語法</span><span class="sxs-lookup"><span data-stu-id="55186-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55186-105">參數</span><span class="sxs-lookup"><span data-stu-id="55186-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="55186-106">脫銷實例的指標 `ICorDebugCode` ，如果函式未編譯為 MSIL，則為 null。</span><span class="sxs-lookup"><span data-stu-id="55186-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55186-107">備註</span><span class="sxs-lookup"><span data-stu-id="55186-107">Remarks</span></span>  
 <span data-ttu-id="55186-108">如果在這個函式上允許 [編輯後繼續]，則 `GetILCode` 方法會取得對應于 common language runtime （CLR）中之程式碼編輯版本的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="55186-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55186-109">需求</span><span class="sxs-lookup"><span data-stu-id="55186-109">Requirements</span></span>  
 <span data-ttu-id="55186-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55186-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55186-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55186-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55186-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55186-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55186-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55186-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
