---
title: ICLRStrongName::GetHashFromAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762145"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="251e5-102">ICLRStrongName::GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="251e5-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="251e5-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="251e5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="251e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="251e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="251e5-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="251e5-106">在要雜湊之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="251e5-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="251e5-107">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="251e5-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="251e5-108">預設雜湊演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="251e5-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="251e5-109">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="251e5-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="251e5-110">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="251e5-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="251e5-111">脫銷傳回的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="251e5-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="251e5-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="251e5-112">Return Value</span></span>  
 <span data-ttu-id="251e5-113">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="251e5-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251e5-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="251e5-114">Requirements</span></span>  
 <span data-ttu-id="251e5-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="251e5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251e5-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="251e5-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="251e5-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="251e5-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="251e5-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251e5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="251e5-119">See also</span></span>

- [<span data-ttu-id="251e5-120">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="251e5-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="251e5-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="251e5-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
