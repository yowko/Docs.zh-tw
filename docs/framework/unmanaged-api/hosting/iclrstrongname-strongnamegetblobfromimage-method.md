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
ms.openlocfilehash: 82e18db2f5b911f0e7895959119edd7d2c722f3b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763122"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="60c8a-102">ICLRStrongName::StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="60c8a-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="60c8a-103">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="60c8a-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="60c8a-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60c8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="60c8a-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="60c8a-106">在對應的組件資訊清單的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="60c8a-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="60c8a-107">在影像的大小（以位元組為單位） `pbBase` 。</span><span class="sxs-lookup"><span data-stu-id="60c8a-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="60c8a-108">在包含影像之二進位表示的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="60c8a-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="60c8a-109">[in、out]要求的大小上限（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="60c8a-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="60c8a-110">傳回時，為的實際大小（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="60c8a-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60c8a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="60c8a-111">Return Value</span></span>  
 <span data-ttu-id="60c8a-112">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="60c8a-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c8a-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="60c8a-113">Requirements</span></span>  
 <span data-ttu-id="60c8a-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60c8a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c8a-115">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="60c8a-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="60c8a-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="60c8a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60c8a-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c8a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c8a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60c8a-118">See also</span></span>

- [<span data-ttu-id="60c8a-119">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="60c8a-119">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="60c8a-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="60c8a-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
