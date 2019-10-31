---
title: ICorDebugModule::GetAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: 29c9d9dde4776ef729c0bbae7b644171a265e3ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137459"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="335be-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="335be-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="335be-103">取得此模組的包含元件。</span><span class="sxs-lookup"><span data-stu-id="335be-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335be-104">語法</span><span class="sxs-lookup"><span data-stu-id="335be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="335be-105">參數</span><span class="sxs-lookup"><span data-stu-id="335be-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="335be-106">脫銷ICorDebugAssembly 物件的指標，表示包含此模組的元件。</span><span class="sxs-lookup"><span data-stu-id="335be-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="335be-107">需求</span><span class="sxs-lookup"><span data-stu-id="335be-107">Requirements</span></span>  
 <span data-ttu-id="335be-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="335be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="335be-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="335be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="335be-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="335be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="335be-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="335be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
