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
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396290"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="677f4-102">ICorPublishAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="677f4-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="677f4-103">取得此[ICorPublishAppDomain](icorpublishappdomain-interface.md)所表示之應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="677f4-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="677f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="677f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="677f4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="677f4-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="677f4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="677f4-107">脫銷陣列中傳回的寬字元數的指標，包括 null 字元 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="677f4-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="677f4-108">脫銷要在其中儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="677f4-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677f4-109">備註</span><span class="sxs-lookup"><span data-stu-id="677f4-109">Remarks</span></span>  
 <span data-ttu-id="677f4-110">如果 `szName` 為非 null，方法會 `GetName` 將最多 `cchName` 個字元（包括 null 結束字元）複製到 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="677f4-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="677f4-111">如果在中傳回非 null，則 `pcchName` 名稱中的實際字元數目（包括 null 結束字元）會儲存在 `szName` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="677f4-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="677f4-112">`GetName`不論已複製多少個字元，方法都會傳回 S_OK HRESULT。</span><span class="sxs-lookup"><span data-stu-id="677f4-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677f4-113">需求</span><span class="sxs-lookup"><span data-stu-id="677f4-113">Requirements</span></span>  
 <span data-ttu-id="677f4-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="677f4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677f4-115">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="677f4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="677f4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="677f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677f4-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677f4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="677f4-118">See also</span></span>

- [<span data-ttu-id="677f4-119">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="677f4-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
