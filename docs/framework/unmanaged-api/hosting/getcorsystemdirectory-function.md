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
ms.openlocfilehash: 21b01156afceb24ab5c132894fae6922d7b97e59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733291"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="2dee8-102">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="2dee8-102">GetCORSystemDirectory Function</span></span>

<span data-ttu-id="2dee8-103">傳回載入至進程之 common language runtime (CLR) 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2dee8-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="2dee8-104">安裝目錄是完整的，例如 "c:\windows\microsoft.net\framework\v1.0.3705"。</span><span class="sxs-lookup"><span data-stu-id="2dee8-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="2dee8-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="2dee8-105">This function is deprecated.</span></span> <span data-ttu-id="2dee8-106">它是由 .NET Framework 4 中提供的 [ICLRRuntimeInfo：： GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) 方法所取代。</span><span class="sxs-lookup"><span data-stu-id="2dee8-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dee8-107">語法</span><span class="sxs-lookup"><span data-stu-id="2dee8-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2dee8-108">參數</span><span class="sxs-lookup"><span data-stu-id="2dee8-108">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="2dee8-109">擴展緩衝區，其中執行時間會傳回字串，其中包含載入至進程之執行時間的完整安裝目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="2dee8-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="2dee8-110">如果執行時間尚未載入到進程中，此函式會傳回電腦上所安裝執行時間最新版本的適當目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="2dee8-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2dee8-111">在的大小（以位元組為單位） `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="2dee8-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2dee8-112">擴展傳回的字元數 `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="2dee8-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dee8-113">備註</span><span class="sxs-lookup"><span data-stu-id="2dee8-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2dee8-114">請勿在執行 CLR 第4版的進程中使用此函數。</span><span class="sxs-lookup"><span data-stu-id="2dee8-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="2dee8-115">如果電腦上已安裝較早版本的 CLR，此函式會傳回該版本的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2dee8-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dee8-116">需求</span><span class="sxs-lookup"><span data-stu-id="2dee8-116">Requirements</span></span>  

 <span data-ttu-id="2dee8-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2dee8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dee8-118">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2dee8-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2dee8-119">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2dee8-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dee8-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dee8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dee8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dee8-121">See also</span></span>

- [<span data-ttu-id="2dee8-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2dee8-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
