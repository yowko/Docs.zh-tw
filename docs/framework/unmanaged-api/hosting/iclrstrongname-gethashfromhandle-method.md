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
ms.openlocfilehash: e2d71f7c61b02273bdcaf182f6f79ca3c2a2c75f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762069"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="95cc2-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="95cc2-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="95cc2-103">使用指定的雜湊演算法，透過具有指定檔案控制代碼的檔案內容產生雜湊。</span><span class="sxs-lookup"><span data-stu-id="95cc2-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95cc2-104">語法</span><span class="sxs-lookup"><span data-stu-id="95cc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95cc2-105">參數</span><span class="sxs-lookup"><span data-stu-id="95cc2-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="95cc2-106">在要雜湊之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="95cc2-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="95cc2-107">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="95cc2-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="95cc2-108">預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="95cc2-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="95cc2-109">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95cc2-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="95cc2-110">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="95cc2-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="95cc2-111">脫銷傳回之的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="95cc2-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95cc2-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="95cc2-112">Return Value</span></span>  
 <span data-ttu-id="95cc2-113">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="95cc2-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95cc2-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="95cc2-114">Requirements</span></span>  
 <span data-ttu-id="95cc2-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95cc2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95cc2-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="95cc2-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="95cc2-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95cc2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95cc2-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95cc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95cc2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95cc2-119">See also</span></span>

- [<span data-ttu-id="95cc2-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="95cc2-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
