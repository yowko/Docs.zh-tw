---
title: ICLRStrongName::GetHashFromHandle 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: c095c99ee60d6b2ea0e5bce7010a66d40160443d
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899678"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="fbb73-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="fbb73-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="fbb73-103">使用指定的雜湊演算法，透過具有指定檔案控制代碼的檔案內容產生雜湊。</span><span class="sxs-lookup"><span data-stu-id="fbb73-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb73-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbb73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbb73-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbb73-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="fbb73-106">在要雜湊之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="fbb73-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fbb73-107">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="fbb73-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="fbb73-108">預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="fbb73-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fbb73-109">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fbb73-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fbb73-110">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="fbb73-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fbb73-111">脫銷傳回之 `pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="fbb73-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbb73-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="fbb73-112">Return Value</span></span>  
 <span data-ttu-id="fbb73-113">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="fbb73-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb73-114">需求</span><span class="sxs-lookup"><span data-stu-id="fbb73-114">Requirements</span></span>  
 <span data-ttu-id="fbb73-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbb73-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb73-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="fbb73-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fbb73-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fbb73-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbb73-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb73-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb73-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb73-119">See also</span></span>

- [<span data-ttu-id="fbb73-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="fbb73-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
