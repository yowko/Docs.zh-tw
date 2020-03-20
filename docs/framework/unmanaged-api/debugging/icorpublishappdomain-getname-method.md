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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178410"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="7035d-102">ICorPublishAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="7035d-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="7035d-103">獲取此[ICorPublishAppDomain](icorpublishappdomain-interface.md)表示的應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="7035d-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7035d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7035d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7035d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7035d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7035d-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="7035d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7035d-107">[出]陣列中返回的指向寬字元數（包括空字元）的`szName`指標。</span><span class="sxs-lookup"><span data-stu-id="7035d-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="7035d-108">[出]要在其中存儲名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="7035d-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7035d-109">備註</span><span class="sxs-lookup"><span data-stu-id="7035d-109">Remarks</span></span>  
 <span data-ttu-id="7035d-110">如果`szName`為非空，`GetName`則該方法將最多複製到`cchName`字元（包括空結束字元）到`szName`中。</span><span class="sxs-lookup"><span data-stu-id="7035d-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="7035d-111">如果在 中`pcchName`返回非 null，則名稱中（包括空結束字元）中的實際字元數存儲在陣列中`szName`。</span><span class="sxs-lookup"><span data-stu-id="7035d-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="7035d-112">無論`GetName`複製的字元數如何，該方法都會返回S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="7035d-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7035d-113">需求</span><span class="sxs-lookup"><span data-stu-id="7035d-113">Requirements</span></span>  
 <span data-ttu-id="7035d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7035d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7035d-115">**標題：** 科爾普布.idl， 科爾普布.h</span><span class="sxs-lookup"><span data-stu-id="7035d-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7035d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7035d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7035d-117">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7035d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7035d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7035d-118">See also</span></span>

- [<span data-ttu-id="7035d-119">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="7035d-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
