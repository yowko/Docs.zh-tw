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
ms.openlocfilehash: daf5319f5d57f44cb20ce9f28d3c7b84c7015ff6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894910"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="fde39-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="fde39-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="fde39-103">取得這個`ICorDebugAssembly`實例所表示之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="fde39-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde39-104">語法</span><span class="sxs-lookup"><span data-stu-id="fde39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fde39-105">參數</span><span class="sxs-lookup"><span data-stu-id="fde39-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fde39-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="fde39-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fde39-107">脫銷整數的指標，指定名稱的實際長度。</span><span class="sxs-lookup"><span data-stu-id="fde39-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="fde39-108">脫銷儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="fde39-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fde39-109">備註</span><span class="sxs-lookup"><span data-stu-id="fde39-109">Remarks</span></span>  
 <span data-ttu-id="fde39-110">`GetName`方法會傳回元件的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="fde39-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde39-111">需求</span><span class="sxs-lookup"><span data-stu-id="fde39-111">Requirements</span></span>  
 <span data-ttu-id="fde39-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fde39-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fde39-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fde39-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fde39-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fde39-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fde39-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fde39-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
