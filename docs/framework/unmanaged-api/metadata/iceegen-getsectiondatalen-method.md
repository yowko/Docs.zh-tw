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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905472"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="cdcab-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="cdcab-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="cdcab-103">取得指定的區段長度。</span><span class="sxs-lookup"><span data-stu-id="cdcab-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="cdcab-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="cdcab-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcab-105">語法</span><span class="sxs-lookup"><span data-stu-id="cdcab-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdcab-106">參數</span><span class="sxs-lookup"><span data-stu-id="cdcab-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="cdcab-107">[in][資料] 區段將擷取其長度的情況下。</span><span class="sxs-lookup"><span data-stu-id="cdcab-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="cdcab-108">[out]指定的區段傳回的長度。</span><span class="sxs-lookup"><span data-stu-id="cdcab-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdcab-109">備註</span><span class="sxs-lookup"><span data-stu-id="cdcab-109">Remarks</span></span>  
 <span data-ttu-id="cdcab-110">呼叫`GetSectionDataLen`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="cdcab-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdcab-111">需求</span><span class="sxs-lookup"><span data-stu-id="cdcab-111">Requirements</span></span>  
 <span data-ttu-id="cdcab-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cdcab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdcab-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cdcab-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdcab-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cdcab-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdcab-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdcab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdcab-116">See also</span></span>

- [<span data-ttu-id="cdcab-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="cdcab-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
