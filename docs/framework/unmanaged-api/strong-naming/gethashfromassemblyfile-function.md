---
title: GetHashFromAssemblyFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: caefc9773b0d208f8b20847b664f7bc017d2c076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730990"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="0c8b7-102">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="0c8b7-102">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="0c8b7-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="0c8b7-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-104">This function has been deprecated.</span></span> <span data-ttu-id="0c8b7-105">請改用 [ICLRStrongName：： GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8b7-106">語法</span><span class="sxs-lookup"><span data-stu-id="0c8b7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8b7-107">參數</span><span class="sxs-lookup"><span data-stu-id="0c8b7-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="0c8b7-108">在要雜湊處理之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0c8b7-109">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="0c8b7-110">使用零作為預設雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0c8b7-111">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0c8b7-112">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0c8b7-113">擴展傳回的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8b7-114">需求</span><span class="sxs-lookup"><span data-stu-id="0c8b7-114">Requirements</span></span>  

 <span data-ttu-id="0c8b7-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c8b7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8b7-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="0c8b7-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0c8b7-117">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0c8b7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c8b7-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8b7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c8b7-119">See also</span></span>

- [<span data-ttu-id="0c8b7-120">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="0c8b7-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="0c8b7-121">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="0c8b7-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="0c8b7-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="0c8b7-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
