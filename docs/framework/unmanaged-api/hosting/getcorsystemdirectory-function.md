---
title: GetCORSystemDirectory 函式
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178197"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="831de-102">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="831de-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="831de-103">返回載入到進程中的通用語言運行時 （CLR） 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="831de-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="831de-104">安裝目錄完全限定，例如，"c：_windows_microsoft.net_framework_v1.0.3705"。</span><span class="sxs-lookup"><span data-stu-id="831de-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="831de-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="831de-105">This function is deprecated.</span></span> <span data-ttu-id="831de-106">它被[ICLRRuntimeInfo 取代：獲取](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md).NET 框架 4 中提供的 RuntimeDirectory 方法。</span><span class="sxs-lookup"><span data-stu-id="831de-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="831de-107">語法</span><span class="sxs-lookup"><span data-stu-id="831de-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="831de-108">參數</span><span class="sxs-lookup"><span data-stu-id="831de-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="831de-109">[出]運行時返回一個字串，其中包含載入到進程的運行時安裝目錄的完全限定名稱。</span><span class="sxs-lookup"><span data-stu-id="831de-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="831de-110">如果運行時尚未載入到進程中，該函數將返回電腦上安裝的最新版本的運行時的相應目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="831de-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="831de-111">[在]的大小（以位元組為單位）的大小`pbuffer`。</span><span class="sxs-lookup"><span data-stu-id="831de-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="831de-112">[出]中`pbuffer`返回的字元數。</span><span class="sxs-lookup"><span data-stu-id="831de-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="831de-113">備註</span><span class="sxs-lookup"><span data-stu-id="831de-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="831de-114">請勿在運行 CLR 版本 4 的進程中使用此功能。</span><span class="sxs-lookup"><span data-stu-id="831de-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="831de-115">如果電腦上安裝了 CLR 的早期版本，則此功能將返回該版本的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="831de-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="831de-116">需求</span><span class="sxs-lookup"><span data-stu-id="831de-116">Requirements</span></span>  
 <span data-ttu-id="831de-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="831de-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="831de-118">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="831de-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="831de-119">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="831de-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="831de-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="831de-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831de-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="831de-121">See also</span></span>

- [<span data-ttu-id="831de-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="831de-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
