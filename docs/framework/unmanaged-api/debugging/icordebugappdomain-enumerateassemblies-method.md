---
title: ICorDebugAppDomain::EnumerateAssemblies 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ce95daaee3c74ac57b107ab8bcb23d41e42cabb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466644"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="c4792-102">ICorDebugAppDomain::EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="c4792-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="c4792-103">取得組件的列舉值，應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c4792-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4792-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4792-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4792-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4792-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="c4792-106">[out]ICorDebugAssemblyEnum 物件的列舉程式的應用程式定義域中的組件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c4792-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4792-107">需求</span><span class="sxs-lookup"><span data-stu-id="c4792-107">Requirements</span></span>  
 <span data-ttu-id="c4792-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4792-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4792-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4792-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4792-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4792-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4792-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4792-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
