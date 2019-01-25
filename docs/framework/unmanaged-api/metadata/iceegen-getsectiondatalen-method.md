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
ms.openlocfilehash: aec97ef36b73b1b789c819c4bca516d13ecf1051
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631200"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="ec9ee-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="ec9ee-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="ec9ee-103">取得指定的區段長度。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="ec9ee-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec9ee-105">語法</span><span class="sxs-lookup"><span data-stu-id="ec9ee-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec9ee-106">參數</span><span class="sxs-lookup"><span data-stu-id="ec9ee-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ec9ee-107">[in][資料] 區段將擷取其長度的情況下。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="ec9ee-108">[out]指定的區段傳回的長度。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec9ee-109">備註</span><span class="sxs-lookup"><span data-stu-id="ec9ee-109">Remarks</span></span>  
 <span data-ttu-id="ec9ee-110">呼叫`GetSectionDataLen`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec9ee-111">需求</span><span class="sxs-lookup"><span data-stu-id="ec9ee-111">Requirements</span></span>  
 <span data-ttu-id="ec9ee-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec9ee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec9ee-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ec9ee-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec9ee-114">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ec9ee-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec9ee-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec9ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9ee-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec9ee-116">See also</span></span>
- [<span data-ttu-id="ec9ee-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ec9ee-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
