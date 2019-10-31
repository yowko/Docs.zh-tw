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
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140348"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="6cb70-102">ICorPublishAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="6cb70-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="6cb70-103">取得此[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)所表示之應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="6cb70-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb70-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cb70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cb70-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cb70-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6cb70-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="6cb70-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6cb70-107">脫銷在 `szName` 陣列中傳回的寬字元數的指標，包括 null 字元。</span><span class="sxs-lookup"><span data-stu-id="6cb70-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="6cb70-108">脫銷要在其中儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="6cb70-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cb70-109">備註</span><span class="sxs-lookup"><span data-stu-id="6cb70-109">Remarks</span></span>  
 <span data-ttu-id="6cb70-110">如果 `szName` 為非 null，則 `GetName` 方法會將最多 `cchName` 個字元（包括 null 結束字元）複製到 `szName`。</span><span class="sxs-lookup"><span data-stu-id="6cb70-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="6cb70-111">如果 `pcchName`傳回非 null，則名稱中的實際字元數目（包括 null 結束字元）會儲存在 `szName` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="6cb70-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="6cb70-112">不論已複製多少個字元，`GetName` 方法都會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6cb70-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb70-113">需求</span><span class="sxs-lookup"><span data-stu-id="6cb70-113">Requirements</span></span>  
 <span data-ttu-id="6cb70-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cb70-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb70-115">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="6cb70-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6cb70-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cb70-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cb70-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cb70-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb70-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6cb70-118">See also</span></span>

- [<span data-ttu-id="6cb70-119">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="6cb70-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
