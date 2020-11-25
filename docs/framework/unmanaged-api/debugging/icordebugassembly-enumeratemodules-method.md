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
ms.openlocfilehash: 6d00d17a5876dd7454b9f89ffa916bc62efb3d0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734123"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="697fd-102">ICorDebugAssembly::EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="697fd-102">ICorDebugAssembly::EnumerateModules Method</span></span>

<span data-ttu-id="697fd-103">取得所包含之模組的列舉值 `ICorDebugAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="697fd-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="697fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="697fd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="697fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="697fd-105">Parameters</span></span>  

 `ppModules`  
 <span data-ttu-id="697fd-106">擴展ICorDebugModuleEnum 介面的位址指標，該介面為列舉值。</span><span class="sxs-lookup"><span data-stu-id="697fd-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="697fd-107">需求</span><span class="sxs-lookup"><span data-stu-id="697fd-107">Requirements</span></span>  

 <span data-ttu-id="697fd-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="697fd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="697fd-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="697fd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="697fd-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="697fd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="697fd-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="697fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
