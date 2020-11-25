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
ms.openlocfilehash: d6b05333b9e02c4202c0fd9bdee9b5c055aa4da3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694356"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="0998d-102">ICorPublishAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="0998d-102">ICorPublishAppDomain::GetName Method</span></span>

<span data-ttu-id="0998d-103">取得此 [ICorPublishAppDomain](icorpublishappdomain-interface.md)所表示之應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="0998d-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0998d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0998d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0998d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0998d-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="0998d-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="0998d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0998d-107">擴展陣列中傳回的寬字元數（包含 null 字元）的指標 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0998d-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="0998d-108">擴展要在其中儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="0998d-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0998d-109">備註</span><span class="sxs-lookup"><span data-stu-id="0998d-109">Remarks</span></span>  

 <span data-ttu-id="0998d-110">如果 `szName` 不是 null，方法會 `GetName` 複製到多 `cchName` 個字元， (包括) 的 null 結束字元 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0998d-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="0998d-111">如果在中傳回非 null，則 `pcchName` 名稱中的實際字元數 (包括 null 結束字元) 會儲存在 `szName` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="0998d-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="0998d-112">`GetName`無論複製了多少個字元，方法都會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="0998d-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0998d-113">需求</span><span class="sxs-lookup"><span data-stu-id="0998d-113">Requirements</span></span>  

 <span data-ttu-id="0998d-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0998d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0998d-115">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="0998d-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0998d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0998d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0998d-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0998d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0998d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0998d-118">See also</span></span>

- [<span data-ttu-id="0998d-119">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="0998d-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
