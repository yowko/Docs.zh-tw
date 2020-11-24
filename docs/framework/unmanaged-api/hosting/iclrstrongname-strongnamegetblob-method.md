---
title: ICLRStrongName::StrongNameGetBlob 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 824dcf89bacec27ced7cc431a9646d00fb879430
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674667"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="76913-102">ICLRStrongName::StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="76913-102">ICLRStrongName::StrongNameGetBlob Method</span></span>

<span data-ttu-id="76913-103">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="76913-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76913-104">語法</span><span class="sxs-lookup"><span data-stu-id="76913-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76913-105">參數</span><span class="sxs-lookup"><span data-stu-id="76913-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="76913-106">在要載入之可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="76913-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="76913-107">在要在其中載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="76913-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="76913-108">[in，out]要求的大小上限（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="76913-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="76913-109">傳回時，的實際大小（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="76913-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76913-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="76913-110">Return Value</span></span>  

 <span data-ttu-id="76913-111">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="76913-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76913-112">需求</span><span class="sxs-lookup"><span data-stu-id="76913-112">Requirements</span></span>  

 <span data-ttu-id="76913-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76913-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76913-114">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="76913-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="76913-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="76913-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76913-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76913-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76913-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76913-117">See also</span></span>

- [<span data-ttu-id="76913-118">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="76913-118">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="76913-119">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="76913-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
