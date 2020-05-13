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
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212538"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="3f28c-102">ICorDebugModule::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="3f28c-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="3f28c-103">取得模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="3f28c-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f28c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f28c-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f28c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f28c-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="3f28c-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3f28c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3f28c-107">在傳回之名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="3f28c-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="3f28c-108">脫銷儲存傳回名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="3f28c-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f28c-109">備註</span><span class="sxs-lookup"><span data-stu-id="3f28c-109">Remarks</span></span>  
 <span data-ttu-id="3f28c-110">`GetName`如果模組的檔案名與磁片上的名稱相符，則此方法會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3f28c-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="3f28c-111">`GetName`如果已製作名稱，則會傳回 S_FALSE HRESULT，例如動態或記憶體中模組。</span><span class="sxs-lookup"><span data-stu-id="3f28c-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f28c-112">需求</span><span class="sxs-lookup"><span data-stu-id="3f28c-112">Requirements</span></span>  
 <span data-ttu-id="3f28c-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f28c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f28c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f28c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f28c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f28c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f28c-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f28c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f28c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f28c-117">See also</span></span>
