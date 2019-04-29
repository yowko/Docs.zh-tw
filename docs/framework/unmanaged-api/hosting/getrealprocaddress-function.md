---
title: GetRealProcAddress 函式
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d4723fbf2311316184cb77c90754d7e037badcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628074"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="b298b-102">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="b298b-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="b298b-103">取得指定從最新安裝 common language runtime (CLR) 版本匯出的函式的位址。</span><span class="sxs-lookup"><span data-stu-id="b298b-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="b298b-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b298b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b298b-105">語法</span><span class="sxs-lookup"><span data-stu-id="b298b-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b298b-106">參數</span><span class="sxs-lookup"><span data-stu-id="b298b-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="b298b-107">[in]函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b298b-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b298b-108">[out]接收函式的位址指標的位置。</span><span class="sxs-lookup"><span data-stu-id="b298b-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b298b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b298b-109">Return Value</span></span>  
 <span data-ttu-id="b298b-110">中所定義 WinError.h，除了 CorError.h 中定義的下列值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="b298b-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="b298b-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="b298b-111">Return code</span></span>|<span data-ttu-id="b298b-112">描述</span><span class="sxs-lookup"><span data-stu-id="b298b-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b298b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b298b-113">S_OK</span></span>|<span data-ttu-id="b298b-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="b298b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b298b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b298b-115">E_POINTER</span></span>|<span data-ttu-id="b298b-116">`ppv` 無效。</span><span class="sxs-lookup"><span data-stu-id="b298b-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="b298b-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="b298b-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="b298b-118">從執行階段不匯出函式。</span><span class="sxs-lookup"><span data-stu-id="b298b-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b298b-119">需求</span><span class="sxs-lookup"><span data-stu-id="b298b-119">Requirements</span></span>  
 <span data-ttu-id="b298b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b298b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b298b-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b298b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b298b-122">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b298b-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b298b-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b298b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b298b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b298b-124">See also</span></span>

- [<span data-ttu-id="b298b-125">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b298b-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
