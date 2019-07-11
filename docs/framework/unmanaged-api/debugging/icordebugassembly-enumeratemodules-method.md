---
title: ICorDebugAssembly::EnumerateModules 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1d8d76084bcf0b5951c6431c6f21f352406050b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737365"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="5eec5-102">ICorDebugAssembly::EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="5eec5-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="5eec5-103">取得列舉值中包含的模組`ICorDebugAssembly`。</span><span class="sxs-lookup"><span data-stu-id="5eec5-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eec5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5eec5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5eec5-105">參數</span><span class="sxs-lookup"><span data-stu-id="5eec5-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="5eec5-106">[out]ICorDebugModuleEnum 介面是列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5eec5-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eec5-107">需求</span><span class="sxs-lookup"><span data-stu-id="5eec5-107">Requirements</span></span>  
 <span data-ttu-id="5eec5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5eec5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eec5-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5eec5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5eec5-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5eec5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5eec5-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eec5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
