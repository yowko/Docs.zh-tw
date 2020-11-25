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
ms.openlocfilehash: 0a15a4d237f63da54615ee1801e6cd39620e8274
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727857"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="f237f-102">ICLRStrongName::GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="f237f-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>

<span data-ttu-id="f237f-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="f237f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f237f-104">語法</span><span class="sxs-lookup"><span data-stu-id="f237f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f237f-105">參數</span><span class="sxs-lookup"><span data-stu-id="f237f-105">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="f237f-106">在要雜湊處理之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f237f-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f237f-107">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="f237f-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f237f-108">使用零作為預設雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="f237f-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f237f-109">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f237f-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f237f-110">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="f237f-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f237f-111">擴展傳回的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="f237f-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f237f-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f237f-112">Return Value</span></span>  

 <span data-ttu-id="f237f-113">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="f237f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f237f-114">需求</span><span class="sxs-lookup"><span data-stu-id="f237f-114">Requirements</span></span>  

 <span data-ttu-id="f237f-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f237f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f237f-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="f237f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f237f-117">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f237f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f237f-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f237f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f237f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f237f-119">See also</span></span>

- [<span data-ttu-id="f237f-120">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="f237f-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="f237f-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f237f-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
