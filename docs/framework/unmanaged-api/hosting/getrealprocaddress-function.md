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
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178166"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="e66cf-102">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="e66cf-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="e66cf-103">獲取從最新安裝的通用語言運行時 （CLR） 匯出的指定函數的位址。</span><span class="sxs-lookup"><span data-stu-id="e66cf-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="e66cf-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="e66cf-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66cf-105">語法</span><span class="sxs-lookup"><span data-stu-id="e66cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e66cf-106">參數</span><span class="sxs-lookup"><span data-stu-id="e66cf-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="e66cf-107">[在]函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e66cf-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e66cf-108">[出]接收指向函數位址的指標的位置。</span><span class="sxs-lookup"><span data-stu-id="e66cf-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e66cf-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e66cf-109">Return Value</span></span>  
 <span data-ttu-id="e66cf-110">此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及 CorError.h 中定義的以下值。</span><span class="sxs-lookup"><span data-stu-id="e66cf-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="e66cf-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="e66cf-111">Return code</span></span>|<span data-ttu-id="e66cf-112">描述</span><span class="sxs-lookup"><span data-stu-id="e66cf-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e66cf-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e66cf-113">S_OK</span></span>|<span data-ttu-id="e66cf-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="e66cf-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e66cf-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e66cf-115">E_POINTER</span></span>|<span data-ttu-id="e66cf-116">`ppv` 無效。</span><span class="sxs-lookup"><span data-stu-id="e66cf-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="e66cf-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="e66cf-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="e66cf-118">函數不會從運行時匯出。</span><span class="sxs-lookup"><span data-stu-id="e66cf-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e66cf-119">需求</span><span class="sxs-lookup"><span data-stu-id="e66cf-119">Requirements</span></span>  
 <span data-ttu-id="e66cf-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e66cf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66cf-121">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e66cf-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e66cf-122">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e66cf-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e66cf-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e66cf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66cf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e66cf-124">See also</span></span>

- [<span data-ttu-id="e66cf-125">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="e66cf-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
