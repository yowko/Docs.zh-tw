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
ms.openlocfilehash: 68bfdb2f66147b54c75b8f577a01278016e248b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685730"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="761b8-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="761b8-102">ICLRStrongName::GetHashFromHandle Method</span></span>

<span data-ttu-id="761b8-103">使用指定的雜湊演算法，產生具有指定檔案控制代碼之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="761b8-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="761b8-104">語法</span><span class="sxs-lookup"><span data-stu-id="761b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="761b8-105">參數</span><span class="sxs-lookup"><span data-stu-id="761b8-105">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="761b8-106">在要雜湊處理之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="761b8-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="761b8-107">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="761b8-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="761b8-108">針對預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="761b8-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="761b8-109">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="761b8-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="761b8-110">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="761b8-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="761b8-111">擴展傳回之的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="761b8-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="761b8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="761b8-112">Return Value</span></span>  

 <span data-ttu-id="761b8-113">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="761b8-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="761b8-114">需求</span><span class="sxs-lookup"><span data-stu-id="761b8-114">Requirements</span></span>  

 <span data-ttu-id="761b8-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="761b8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="761b8-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="761b8-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="761b8-117">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="761b8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="761b8-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="761b8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761b8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="761b8-119">See also</span></span>

- [<span data-ttu-id="761b8-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="761b8-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
