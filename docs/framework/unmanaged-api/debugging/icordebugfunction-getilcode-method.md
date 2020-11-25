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
ms.openlocfilehash: b7d3fbafaab6d43fa89d45855628dbd6b9ab81e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696215"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="af4a8-102">ICorDebugFunction::GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="af4a8-102">ICorDebugFunction::GetILCode Method</span></span>

<span data-ttu-id="af4a8-103">取得代表與此 ICorDebugFunction 物件相關聯之 Microsoft 中繼語言 (MSIL) 程式碼的 ICorDebugCode 實例。</span><span class="sxs-lookup"><span data-stu-id="af4a8-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="af4a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af4a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="af4a8-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="af4a8-106">擴展實例的指標 `ICorDebugCode` ，如果函式未編譯成 MSIL，則為 null。</span><span class="sxs-lookup"><span data-stu-id="af4a8-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af4a8-107">備註</span><span class="sxs-lookup"><span data-stu-id="af4a8-107">Remarks</span></span>  

 <span data-ttu-id="af4a8-108">如果已允許此函式的 [編輯後繼續]，則此 `GetILCode` 方法會在 common language runtime (CLR) 中，取得對應到此函式之程式碼編輯版本的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="af4a8-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af4a8-109">需求</span><span class="sxs-lookup"><span data-stu-id="af4a8-109">Requirements</span></span>  

 <span data-ttu-id="af4a8-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af4a8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af4a8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af4a8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af4a8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af4a8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af4a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
