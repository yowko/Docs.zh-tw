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
ms.openlocfilehash: c7f04364cc52bd38d7d2659d1d188c5fd783ad01
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899756"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="0b40f-102">ICLRStrongName::StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="0b40f-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="0b40f-103">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0b40f-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b40f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b40f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b40f-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b40f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0b40f-106">在要載入之可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="0b40f-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="0b40f-107">在要載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0b40f-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="0b40f-108">[in、out]`pbBlob`的要求大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0b40f-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="0b40f-109">傳回時，`pbBlob`的實際大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0b40f-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b40f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0b40f-110">Return Value</span></span>  
 <span data-ttu-id="0b40f-111">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="0b40f-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b40f-112">需求</span><span class="sxs-lookup"><span data-stu-id="0b40f-112">Requirements</span></span>  
 <span data-ttu-id="0b40f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b40f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b40f-114">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="0b40f-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0b40f-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0b40f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b40f-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b40f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b40f-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b40f-117">See also</span></span>

- [<span data-ttu-id="0b40f-118">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="0b40f-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="0b40f-119">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="0b40f-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
