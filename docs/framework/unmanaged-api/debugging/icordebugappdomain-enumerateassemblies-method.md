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
ms.openlocfilehash: 6bacd93baae3f0c0b70c4b910e8130551b4f3e48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738059"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="2f096-102">ICorDebugAppDomain::EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="2f096-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="2f096-103">取得組件的列舉值，應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="2f096-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f096-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f096-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f096-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f096-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="2f096-106">[out]ICorDebugAssemblyEnum 物件的列舉程式的應用程式定義域中的組件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2f096-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f096-107">需求</span><span class="sxs-lookup"><span data-stu-id="2f096-107">Requirements</span></span>  
 <span data-ttu-id="2f096-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f096-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f096-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f096-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f096-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f096-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f096-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f096-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
