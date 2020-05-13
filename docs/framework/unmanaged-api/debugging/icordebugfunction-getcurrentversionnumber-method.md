---
title: ICorDebugFunction::GetCurrentVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212902"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="0f675-102">ICorDebugFunction::GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="0f675-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="0f675-103">取得此 ICorDebugFunction 物件所代表之函式的最新編輯版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0f675-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f675-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f675-105">參數</span><span class="sxs-lookup"><span data-stu-id="0f675-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="0f675-106">脫銷整數值的指標，這是對此函式進行最新編輯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0f675-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f675-107">備註</span><span class="sxs-lookup"><span data-stu-id="0f675-107">Remarks</span></span>  
 <span data-ttu-id="0f675-108">對此函式進行的最新編輯版本號碼，可能會大於函式本身的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0f675-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="0f675-109">請使用[ICorDebugFunction2：： GetVersionNumber](icordebugfunction2-getversionnumber-method.md)方法或[ICorDebugCode：： GetVersionNumber](icordebugcode-getversionnumber-method.md)方法來取出函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0f675-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f675-110">需求</span><span class="sxs-lookup"><span data-stu-id="0f675-110">Requirements</span></span>  
 <span data-ttu-id="0f675-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f675-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f675-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f675-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f675-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f675-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f675-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f675-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
