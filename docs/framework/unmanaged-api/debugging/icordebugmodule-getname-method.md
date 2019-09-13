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
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894982"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="c6712-102">ICorDebugModule::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="c6712-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="c6712-103">取得模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="c6712-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6712-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6712-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6712-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6712-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="c6712-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c6712-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c6712-107">在傳回之名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="c6712-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c6712-108">脫銷儲存傳回名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6712-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6712-109">備註</span><span class="sxs-lookup"><span data-stu-id="c6712-109">Remarks</span></span>  
 <span data-ttu-id="c6712-110">如果`GetName`模組的檔案名與磁片上的名稱相符，此方法會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="c6712-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="c6712-111">`GetName`如果已製作名稱，則會傳回 S_FALSE HRESULT，例如針對動態或記憶體中的模組。</span><span class="sxs-lookup"><span data-stu-id="c6712-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6712-112">需求</span><span class="sxs-lookup"><span data-stu-id="c6712-112">Requirements</span></span>  
 <span data-ttu-id="c6712-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6712-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6712-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6712-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6712-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6712-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6712-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6712-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6712-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6712-117">See also</span></span>
