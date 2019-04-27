---
title: ICorDebugModule::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b39467c067e50f2d553b35a41b0f783e0fc82156
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988012"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="b71fd-102">ICorDebugModule::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="b71fd-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="b71fd-103">取得模組的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b71fd-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b71fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b71fd-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b71fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="b71fd-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="b71fd-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b71fd-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b71fd-107">[in]傳回名稱的長度指標。</span><span class="sxs-lookup"><span data-stu-id="b71fd-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b71fd-108">[out]陣列，其中會儲存傳回的名稱。</span><span class="sxs-lookup"><span data-stu-id="b71fd-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b71fd-109">備註</span><span class="sxs-lookup"><span data-stu-id="b71fd-109">Remarks</span></span>  
 <span data-ttu-id="b71fd-110">`GetName`方法會傳回 S_OK HRESULT，如果模組的檔案名稱符合磁碟上的名稱。</span><span class="sxs-lookup"><span data-stu-id="b71fd-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="b71fd-111">`GetName` 如果名稱是製作，例如動態或記憶體中的模組，會傳回 S_FALSE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b71fd-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b71fd-112">需求</span><span class="sxs-lookup"><span data-stu-id="b71fd-112">Requirements</span></span>  
 <span data-ttu-id="b71fd-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b71fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b71fd-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b71fd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b71fd-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b71fd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b71fd-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b71fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71fd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b71fd-117">See also</span></span>
