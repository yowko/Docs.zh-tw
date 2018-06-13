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
ms.openlocfilehash: 13137dcf7c2edd96397916cc7db905c9e48a3d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401596"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="5e27c-102">ICorDebugAppDomain::EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="5e27c-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="5e27c-103">取得應用程式定義域中之組件列舉值。</span><span class="sxs-lookup"><span data-stu-id="5e27c-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e27c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e27c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e27c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e27c-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="5e27c-106">[out]ICorDebugAssemblyEnum 物件，應用程式定義域中的組件的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5e27c-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e27c-107">需求</span><span class="sxs-lookup"><span data-stu-id="5e27c-107">Requirements</span></span>  
 <span data-ttu-id="5e27c-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e27c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e27c-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e27c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e27c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e27c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e27c-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e27c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
