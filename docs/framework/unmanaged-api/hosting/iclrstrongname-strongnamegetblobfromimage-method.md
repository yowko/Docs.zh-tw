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
ms.openlocfilehash: ad5fa510a17a3ce823ff90c4131b349b0d9efd39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671742"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="2455c-102">ICLRStrongName::StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="2455c-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>

<span data-ttu-id="2455c-103">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="2455c-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2455c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2455c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2455c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2455c-105">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="2455c-106">在對應的組件資訊清單的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="2455c-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2455c-107">在影像的大小（以位元組為單位） `pbBase` 。</span><span class="sxs-lookup"><span data-stu-id="2455c-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="2455c-108">在包含影像之二進位表示的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2455c-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="2455c-109">[in，out]要求的大小上限（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="2455c-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="2455c-110">傳回時，的實際大小（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="2455c-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2455c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2455c-111">Return Value</span></span>  

 <span data-ttu-id="2455c-112">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="2455c-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2455c-113">需求</span><span class="sxs-lookup"><span data-stu-id="2455c-113">Requirements</span></span>  

 <span data-ttu-id="2455c-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2455c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2455c-115">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="2455c-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2455c-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2455c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2455c-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2455c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2455c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2455c-118">See also</span></span>

- [<span data-ttu-id="2455c-119">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="2455c-119">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="2455c-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2455c-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
