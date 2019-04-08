---
title: ICeeGen::GetSectionDataLen 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca01f78cf46d4f7543b949c820eb6b1971687e23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198708"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="141ae-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="141ae-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="141ae-103">取得指定的區段長度。</span><span class="sxs-lookup"><span data-stu-id="141ae-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="141ae-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="141ae-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141ae-105">語法</span><span class="sxs-lookup"><span data-stu-id="141ae-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="141ae-106">參數</span><span class="sxs-lookup"><span data-stu-id="141ae-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="141ae-107">[in][資料] 區段將擷取其長度的情況下。</span><span class="sxs-lookup"><span data-stu-id="141ae-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="141ae-108">[out]指定的區段傳回的長度。</span><span class="sxs-lookup"><span data-stu-id="141ae-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="141ae-109">備註</span><span class="sxs-lookup"><span data-stu-id="141ae-109">Remarks</span></span>  
 <span data-ttu-id="141ae-110">呼叫`GetSectionDataLen`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="141ae-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="141ae-111">需求</span><span class="sxs-lookup"><span data-stu-id="141ae-111">Requirements</span></span>  
 <span data-ttu-id="141ae-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="141ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="141ae-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="141ae-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="141ae-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="141ae-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="141ae-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="141ae-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="141ae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="141ae-116">See also</span></span>

- [<span data-ttu-id="141ae-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="141ae-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
