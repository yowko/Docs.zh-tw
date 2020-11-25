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
ms.openlocfilehash: e0ae11ee24a5e25fb439d5c502c4cda5bcb6a80e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710255"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="5e61d-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5e61d-102">ICorDebugModule::GetAssembly Method</span></span>

<span data-ttu-id="5e61d-103">取得此模組的包含元件。</span><span class="sxs-lookup"><span data-stu-id="5e61d-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e61d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e61d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e61d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e61d-105">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="5e61d-106">擴展ICorDebugAssembly 物件的指標，代表包含此模組的元件。</span><span class="sxs-lookup"><span data-stu-id="5e61d-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e61d-107">需求</span><span class="sxs-lookup"><span data-stu-id="5e61d-107">Requirements</span></span>  

 <span data-ttu-id="5e61d-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e61d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e61d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e61d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e61d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e61d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e61d-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e61d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
