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
ms.openlocfilehash: e94bfe6151ed42886355423a838f21e13748ec61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685769"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="9ad03-102">ICLRStrongName::GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="9ad03-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="9ad03-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="9ad03-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad03-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ad03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ad03-105">參數</span><span class="sxs-lookup"><span data-stu-id="9ad03-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9ad03-106">在要雜湊處理之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9ad03-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="9ad03-107">此參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="9ad03-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9ad03-108">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="9ad03-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9ad03-109">使用零作為預設雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="9ad03-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9ad03-110">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9ad03-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9ad03-111">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="9ad03-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9ad03-112">擴展傳回的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="9ad03-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ad03-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="9ad03-113">Return Value</span></span>  

 <span data-ttu-id="9ad03-114">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="9ad03-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad03-115">需求</span><span class="sxs-lookup"><span data-stu-id="9ad03-115">Requirements</span></span>  

 <span data-ttu-id="9ad03-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ad03-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad03-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="9ad03-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ad03-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9ad03-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ad03-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad03-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ad03-120">See also</span></span>

- [<span data-ttu-id="9ad03-121">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="9ad03-121">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="9ad03-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="9ad03-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
