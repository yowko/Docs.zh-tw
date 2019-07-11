---
title: ICorDebugAssembly::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38542ec28cce9687dc3ed824f9d449f3070976da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737308"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="af398-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="af398-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="af398-103">取得組件名稱這`ICorDebugAssembly`執行個體表示。</span><span class="sxs-lookup"><span data-stu-id="af398-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af398-104">語法</span><span class="sxs-lookup"><span data-stu-id="af398-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af398-105">參數</span><span class="sxs-lookup"><span data-stu-id="af398-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="af398-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="af398-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="af398-107">[out]指定名稱的實際長度的整數指標。</span><span class="sxs-lookup"><span data-stu-id="af398-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="af398-108">[out]陣列，其中儲存的名稱。</span><span class="sxs-lookup"><span data-stu-id="af398-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af398-109">備註</span><span class="sxs-lookup"><span data-stu-id="af398-109">Remarks</span></span>  
 <span data-ttu-id="af398-110">`GetName`方法會傳回組件的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="af398-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af398-111">需求</span><span class="sxs-lookup"><span data-stu-id="af398-111">Requirements</span></span>  
 <span data-ttu-id="af398-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af398-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af398-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af398-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af398-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af398-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af398-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af398-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
