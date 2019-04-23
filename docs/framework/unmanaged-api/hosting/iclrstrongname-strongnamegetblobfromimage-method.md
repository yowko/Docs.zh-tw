---
title: ICLRStrongName::StrongNameGetBlobFromImage 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa83f55a03ebfff9ae88217b01c86272bf0de93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178967"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="a4c6c-102">ICLRStrongName::StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="a4c6c-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="a4c6c-103">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c6c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4c6c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c6c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4c6c-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="a4c6c-106">[in]對應的組件資訊清單的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a4c6c-107">[in]大小 （位元組），在映像的`pbBase`。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="a4c6c-108">[in]包含影像的二進位表示法的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="a4c6c-109">[in、 out]所要求大小上限，以位元組為單位， `pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="a4c6c-110">傳回時，實際的大小，以位元組為單位的`pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4c6c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4c6c-111">Return Value</span></span>  
 <span data-ttu-id="a4c6c-112">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c6c-113">需求</span><span class="sxs-lookup"><span data-stu-id="a4c6c-113">Requirements</span></span>  
 <span data-ttu-id="a4c6c-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4c6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c6c-115">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a4c6c-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4c6c-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a4c6c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4c6c-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c6c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4c6c-118">See also</span></span>

- [<span data-ttu-id="a4c6c-119">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="a4c6c-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="a4c6c-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="a4c6c-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
