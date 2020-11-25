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
ms.openlocfilehash: 386913f8c81ff3c8b98bb0cab4ffc101a4f6085f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723320"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="33038-102">ICorDebugAppDomain::EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="33038-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>

<span data-ttu-id="33038-103">取得應用程式域中元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="33038-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33038-104">語法</span><span class="sxs-lookup"><span data-stu-id="33038-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33038-105">參數</span><span class="sxs-lookup"><span data-stu-id="33038-105">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="33038-106">擴展ICorDebugAssemblyEnum 物件位址的指標，該物件是應用程式域中元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="33038-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33038-107">需求</span><span class="sxs-lookup"><span data-stu-id="33038-107">Requirements</span></span>  

 <span data-ttu-id="33038-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33038-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33038-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33038-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33038-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33038-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33038-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33038-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
