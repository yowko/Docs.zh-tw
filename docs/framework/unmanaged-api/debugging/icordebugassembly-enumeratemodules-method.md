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
ms.openlocfilehash: 12dc5466d5be73b327f171c389c41c55901f2915
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894947"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="66019-102">ICorDebugAssembly::EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="66019-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="66019-103">取得包含在中之模組的列舉值`ICorDebugAssembly`。</span><span class="sxs-lookup"><span data-stu-id="66019-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66019-104">語法</span><span class="sxs-lookup"><span data-stu-id="66019-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66019-105">參數</span><span class="sxs-lookup"><span data-stu-id="66019-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="66019-106">脫銷做為列舉值之 ICorDebugModuleEnum 介面位址的指標。</span><span class="sxs-lookup"><span data-stu-id="66019-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66019-107">需求</span><span class="sxs-lookup"><span data-stu-id="66019-107">Requirements</span></span>  
 <span data-ttu-id="66019-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66019-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66019-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66019-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66019-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66019-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66019-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66019-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
