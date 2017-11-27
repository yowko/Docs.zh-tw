---
title: "GetCORSystemDirectory 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 802e9a7bd4e6caedd657a8e8cf0132d75b4cbc2e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="77d49-102">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="77d49-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="77d49-103">傳回 common language runtime (CLR) 載入到處理程序的安裝的目錄。</span><span class="sxs-lookup"><span data-stu-id="77d49-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="77d49-104">安裝目錄是完整名稱，例如，"c:\windows\microsoft.net\framework\v1.0.3705"。</span><span class="sxs-lookup"><span data-stu-id="77d49-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="77d49-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="77d49-105">This function is deprecated.</span></span> <span data-ttu-id="77d49-106">被取代[iclrruntimeinfo:: Getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)方法中提供[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77d49-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d49-107">語法</span><span class="sxs-lookup"><span data-stu-id="77d49-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="77d49-108">參數</span><span class="sxs-lookup"><span data-stu-id="77d49-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="77d49-109">[out]在其中執行階段會傳回字串，包含載入到處理序的執行階段安裝目錄的完整格式的名稱緩衝區。</span><span class="sxs-lookup"><span data-stu-id="77d49-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="77d49-110">如果執行階段尚未載入到程序，則函數會傳回最新版本的執行階段電腦上安裝適當的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="77d49-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="77d49-111">[in]大小，以位元組為單位的`pbuffer`。</span><span class="sxs-lookup"><span data-stu-id="77d49-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="77d49-112">[out]傳入的字元數`pbuffer`。</span><span class="sxs-lookup"><span data-stu-id="77d49-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d49-113">備註</span><span class="sxs-lookup"><span data-stu-id="77d49-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="77d49-114">請勿使用此函式中執行的 CLR 版本 4 的處理序。</span><span class="sxs-lookup"><span data-stu-id="77d49-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="77d49-115">如果在電腦上已安裝舊版的 clr，此函數會傳回該版本的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="77d49-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d49-116">需求</span><span class="sxs-lookup"><span data-stu-id="77d49-116">Requirements</span></span>  
 <span data-ttu-id="77d49-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77d49-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d49-118">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77d49-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77d49-119">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77d49-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77d49-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d49-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d49-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77d49-121">See Also</span></span>  
 [<span data-ttu-id="77d49-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="77d49-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
