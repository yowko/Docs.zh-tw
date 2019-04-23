---
title: ICorPublishAppDomain::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5de74b52caee27a1a12cff4a7f9165a07e961ce7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072780"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="3afce-102">ICorPublishAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="3afce-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="3afce-103">取得表示此應用程式定義域的名稱[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="3afce-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3afce-104">語法</span><span class="sxs-lookup"><span data-stu-id="3afce-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3afce-105">參數</span><span class="sxs-lookup"><span data-stu-id="3afce-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3afce-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3afce-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3afce-107">[out]包含在傳回的 null 字元的寬字元數目的指標`szName`陣列。</span><span class="sxs-lookup"><span data-stu-id="3afce-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="3afce-108">[out]用來儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="3afce-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3afce-109">備註</span><span class="sxs-lookup"><span data-stu-id="3afce-109">Remarks</span></span>  
 <span data-ttu-id="3afce-110">如果`szName`為非 null`GetName`方法會複製達`cchName`字元 （包括 null 結束字元） 到`szName`。</span><span class="sxs-lookup"><span data-stu-id="3afce-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="3afce-111">如果非 null 會傳入`pcchName`，實際數目的名稱 （包括 null 結束字元） 中的字元會儲存在`szName`陣列。</span><span class="sxs-lookup"><span data-stu-id="3afce-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="3afce-112">`GetName`方法會傳回 S_OK HRESULT，不論已複製的字元數。</span><span class="sxs-lookup"><span data-stu-id="3afce-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3afce-113">需求</span><span class="sxs-lookup"><span data-stu-id="3afce-113">Requirements</span></span>  
 <span data-ttu-id="3afce-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3afce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3afce-115">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3afce-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3afce-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3afce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3afce-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3afce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afce-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3afce-118">See also</span></span>

- [<span data-ttu-id="3afce-119">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="3afce-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
