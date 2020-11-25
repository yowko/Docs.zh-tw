---
title: GetRequestedRuntimeVersion 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711633"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="07a8c-102">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="07a8c-102">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="07a8c-103">取得指定的應用程式所要求之 common language runtime (CLR) 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="07a8c-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="07a8c-104">如果未安裝該版本，則會取得在要求的版本之前安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="07a8c-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="07a8c-105">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="07a8c-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a8c-106">語法</span><span class="sxs-lookup"><span data-stu-id="07a8c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07a8c-107">參數</span><span class="sxs-lookup"><span data-stu-id="07a8c-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="07a8c-108">在應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="07a8c-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="07a8c-109">擴展在成功完成時包含版本號碼字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="07a8c-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="07a8c-110">在版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="07a8c-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="07a8c-111">擴展版本號碼字串的長度指標。</span><span class="sxs-lookup"><span data-stu-id="07a8c-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07a8c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="07a8c-112">Return Value</span></span>  

 <span data-ttu-id="07a8c-113">除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。</span><span class="sxs-lookup"><span data-stu-id="07a8c-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="07a8c-114">傳回碼</span><span class="sxs-lookup"><span data-stu-id="07a8c-114">Return code</span></span>|<span data-ttu-id="07a8c-115">描述</span><span class="sxs-lookup"><span data-stu-id="07a8c-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="07a8c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="07a8c-116">S_OK</span></span>|<span data-ttu-id="07a8c-117">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="07a8c-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="07a8c-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="07a8c-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="07a8c-119">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="07a8c-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="07a8c-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="07a8c-120">E_POINTER</span></span>|<span data-ttu-id="07a8c-121">`pdwLength` 為 null。</span><span class="sxs-lookup"><span data-stu-id="07a8c-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07a8c-122">需求</span><span class="sxs-lookup"><span data-stu-id="07a8c-122">Requirements</span></span>  

 <span data-ttu-id="07a8c-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07a8c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a8c-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="07a8c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07a8c-125">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07a8c-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07a8c-126">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a8c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a8c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07a8c-127">See also</span></span>

- [<span data-ttu-id="07a8c-128">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="07a8c-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="07a8c-129">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="07a8c-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="07a8c-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="07a8c-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
