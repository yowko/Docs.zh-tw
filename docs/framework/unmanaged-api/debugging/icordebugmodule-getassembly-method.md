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
ms.openlocfilehash: 86e2b28448caf2a872e44490e8ee4763b056ed44
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206959"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="9df4f-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="9df4f-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="9df4f-103">取得此模組的包含元件。</span><span class="sxs-lookup"><span data-stu-id="9df4f-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9df4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9df4f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9df4f-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="9df4f-106">脫銷ICorDebugAssembly 物件的指標，表示包含此模組的元件。</span><span class="sxs-lookup"><span data-stu-id="9df4f-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9df4f-107">需求</span><span class="sxs-lookup"><span data-stu-id="9df4f-107">Requirements</span></span>  
 <span data-ttu-id="9df4f-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9df4f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9df4f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9df4f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9df4f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9df4f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9df4f-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9df4f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
