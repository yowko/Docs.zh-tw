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
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127163"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="61023-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="61023-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="61023-103">取得此 `ICorDebugAssembly` 實例所代表之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="61023-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61023-104">語法</span><span class="sxs-lookup"><span data-stu-id="61023-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61023-105">參數</span><span class="sxs-lookup"><span data-stu-id="61023-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="61023-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="61023-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="61023-107">脫銷整數的指標，指定名稱的實際長度。</span><span class="sxs-lookup"><span data-stu-id="61023-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="61023-108">脫銷儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="61023-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61023-109">備註</span><span class="sxs-lookup"><span data-stu-id="61023-109">Remarks</span></span>  
 <span data-ttu-id="61023-110">`GetName` 方法會傳回元件的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="61023-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61023-111">需求</span><span class="sxs-lookup"><span data-stu-id="61023-111">Requirements</span></span>  
 <span data-ttu-id="61023-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61023-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61023-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61023-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61023-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61023-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61023-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61023-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
