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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78bfc91bdd0f9fa68252c6a07e1362807eb507b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416019"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="ff2a1-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="ff2a1-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="ff2a1-103">取得針對此模組包含組件。</span><span class="sxs-lookup"><span data-stu-id="ff2a1-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff2a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff2a1-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff2a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff2a1-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="ff2a1-106">[out]ICorDebugAssembly 物件，代表包含此模組的組件的指標。</span><span class="sxs-lookup"><span data-stu-id="ff2a1-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2a1-107">需求</span><span class="sxs-lookup"><span data-stu-id="ff2a1-107">Requirements</span></span>  
 <span data-ttu-id="ff2a1-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff2a1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2a1-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff2a1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff2a1-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2a1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2a1-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
