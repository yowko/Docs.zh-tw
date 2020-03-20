---
title: GetFileVersion 函式
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178171"
---
# <a name="getfileversion-function"></a><span data-ttu-id="10f52-102">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="10f52-102">GetFileVersion Function</span></span>
<span data-ttu-id="10f52-103">使用指定的緩衝區獲取指定檔的常見語言運行時 （CLR） 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="10f52-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="10f52-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="10f52-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f52-105">語法</span><span class="sxs-lookup"><span data-stu-id="10f52-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10f52-106">參數</span><span class="sxs-lookup"><span data-stu-id="10f52-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="10f52-107">[在]要檢查的檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="10f52-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="10f52-108">[進出]為返回的版本資訊分配的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="10f52-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="10f52-109">[在]的大小（以寬字元表示`szBuffer`）</span><span class="sxs-lookup"><span data-stu-id="10f52-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="10f52-110">[出]返回`szBuffer`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="10f52-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f52-111">需求</span><span class="sxs-lookup"><span data-stu-id="10f52-111">Requirements</span></span>  
 <span data-ttu-id="10f52-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10f52-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10f52-113">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10f52-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10f52-114">**.NET 框架版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10f52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f52-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10f52-115">See also</span></span>

- [<span data-ttu-id="10f52-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="10f52-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
