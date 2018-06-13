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
ms.openlocfilehash: fe587f6356eec861c39c9eb0aa0b6476e0b9a232
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407515"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="11c81-102">ICorDebugAssembly::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="11c81-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="11c81-103">取得組件的名稱這`ICorDebugAssembly`執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="11c81-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c81-104">語法</span><span class="sxs-lookup"><span data-stu-id="11c81-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11c81-105">參數</span><span class="sxs-lookup"><span data-stu-id="11c81-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="11c81-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="11c81-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="11c81-107">[out]指定名稱的實際長度的整數指標。</span><span class="sxs-lookup"><span data-stu-id="11c81-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="11c81-108">[out]陣列，其中儲存的名稱。</span><span class="sxs-lookup"><span data-stu-id="11c81-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c81-109">備註</span><span class="sxs-lookup"><span data-stu-id="11c81-109">Remarks</span></span>  
 <span data-ttu-id="11c81-110">`GetName`方法會傳回組件的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="11c81-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c81-111">需求</span><span class="sxs-lookup"><span data-stu-id="11c81-111">Requirements</span></span>  
 <span data-ttu-id="11c81-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11c81-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c81-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11c81-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c81-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c81-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c81-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
