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
ms.openlocfilehash: d48106fca6008955409581ad9ac202aebe785cb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733219"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="69b1d-102">GetRealProcAddress 函式</span><span class="sxs-lookup"><span data-stu-id="69b1d-102">GetRealProcAddress Function</span></span>

<span data-ttu-id="69b1d-103">取得所指定函式的位址，該函式會從最新安裝的 common language runtime 版本 (CLR) 匯出。</span><span class="sxs-lookup"><span data-stu-id="69b1d-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="69b1d-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="69b1d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b1d-105">語法</span><span class="sxs-lookup"><span data-stu-id="69b1d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b1d-106">參數</span><span class="sxs-lookup"><span data-stu-id="69b1d-106">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="69b1d-107">在函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="69b1d-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="69b1d-108">擴展接收函數位址指標的位置。</span><span class="sxs-lookup"><span data-stu-id="69b1d-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69b1d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="69b1d-109">Return Value</span></span>  

 <span data-ttu-id="69b1d-110">除了 Corerror.h 中定義的下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。</span><span class="sxs-lookup"><span data-stu-id="69b1d-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="69b1d-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="69b1d-111">Return code</span></span>|<span data-ttu-id="69b1d-112">描述</span><span class="sxs-lookup"><span data-stu-id="69b1d-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="69b1d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="69b1d-113">S_OK</span></span>|<span data-ttu-id="69b1d-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="69b1d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="69b1d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="69b1d-115">E_POINTER</span></span>|<span data-ttu-id="69b1d-116">`ppv` 無效。</span><span class="sxs-lookup"><span data-stu-id="69b1d-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="69b1d-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="69b1d-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="69b1d-118">函式不是從執行時間匯出。</span><span class="sxs-lookup"><span data-stu-id="69b1d-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69b1d-119">需求</span><span class="sxs-lookup"><span data-stu-id="69b1d-119">Requirements</span></span>  

 <span data-ttu-id="69b1d-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69b1d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b1d-121">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="69b1d-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69b1d-122">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69b1d-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69b1d-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b1d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b1d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b1d-124">See also</span></span>

- [<span data-ttu-id="69b1d-125">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="69b1d-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
