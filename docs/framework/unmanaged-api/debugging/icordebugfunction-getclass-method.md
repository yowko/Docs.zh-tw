---
title: ICorDebugFunction::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea71e984be42e3b1a7b4b9fa6df878aca911c412
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501184"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="d9318-102">ICorDebugFunction::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="d9318-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="d9318-103">取得 ICorDebugClass 物件，表示此函式所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="d9318-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9318-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9318-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9318-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9318-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="d9318-106">[out]位址指標`ICorDebugClass`物件，表示類別或 null，此函式不是類別的成員。</span><span class="sxs-lookup"><span data-stu-id="d9318-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9318-107">需求</span><span class="sxs-lookup"><span data-stu-id="d9318-107">Requirements</span></span>  
 <span data-ttu-id="d9318-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9318-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9318-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9318-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9318-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9318-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9318-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9318-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
