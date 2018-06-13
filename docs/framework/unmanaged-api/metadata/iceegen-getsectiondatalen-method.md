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
ms.openlocfilehash: b85cdee4a65e91c51fdb014bdcc4797b99214daf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446127"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="ff690-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="ff690-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="ff690-103">取得指定之區段的長度。</span><span class="sxs-lookup"><span data-stu-id="ff690-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="ff690-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="ff690-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff690-105">語法</span><span class="sxs-lookup"><span data-stu-id="ff690-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff690-106">參數</span><span class="sxs-lookup"><span data-stu-id="ff690-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ff690-107">[in]資料區段，將擷取其長度。</span><span class="sxs-lookup"><span data-stu-id="ff690-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="ff690-108">[out]傳回指定之區段的長度。</span><span class="sxs-lookup"><span data-stu-id="ff690-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff690-109">備註</span><span class="sxs-lookup"><span data-stu-id="ff690-109">Remarks</span></span>  
 <span data-ttu-id="ff690-110">呼叫`GetSectionDataLen`只有當您有不由其他方法處理的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="ff690-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff690-111">需求</span><span class="sxs-lookup"><span data-stu-id="ff690-111">Requirements</span></span>  
 <span data-ttu-id="ff690-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff690-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff690-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff690-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff690-114">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ff690-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff690-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff690-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff690-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff690-116">See Also</span></span>  
 [<span data-ttu-id="ff690-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ff690-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
