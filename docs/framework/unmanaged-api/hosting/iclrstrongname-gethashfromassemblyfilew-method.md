---
title: ICLRStrongName::GetHashFromAssemblyFileW 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 43a5cd57a8eeaba70f1bb1ffb9cab5bb1a067914
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130958"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="d7589-102">ICLRStrongName::GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="d7589-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="d7589-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d7589-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7589-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7589-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7589-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7589-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d7589-106">在要雜湊之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d7589-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="d7589-107">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="d7589-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d7589-108">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="d7589-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d7589-109">預設雜湊演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="d7589-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d7589-110">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d7589-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d7589-111">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="d7589-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d7589-112">脫銷傳回的大小，以位元組為單位，`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="d7589-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7589-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7589-113">Return Value</span></span>  
 <span data-ttu-id="d7589-114">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="d7589-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7589-115">需求</span><span class="sxs-lookup"><span data-stu-id="d7589-115">Requirements</span></span>  
 <span data-ttu-id="d7589-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7589-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7589-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="d7589-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d7589-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d7589-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7589-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7589-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7589-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7589-120">See also</span></span>

- [<span data-ttu-id="d7589-121">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="d7589-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="d7589-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d7589-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
