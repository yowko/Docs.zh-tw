---
title: ICLRMetaHost::EnumerateInstalledRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: f8f67edde7f99878429ca0bbd89aaf52336aa79c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730444"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="adc53-102">ICLRMetaHost::EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="adc53-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="adc53-103">傳回列舉，其中包含安裝在電腦上之每個 common language runtime (CLR) 的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="adc53-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc53-104">語法</span><span class="sxs-lookup"><span data-stu-id="adc53-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adc53-105">參數</span><span class="sxs-lookup"><span data-stu-id="adc53-105">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="adc53-106">擴展 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面的列舉，對應于電腦上安裝的每個 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="adc53-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adc53-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="adc53-107">Return Value</span></span>  

 <span data-ttu-id="adc53-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="adc53-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="adc53-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adc53-109">HRESULT</span></span>|<span data-ttu-id="adc53-110">描述</span><span class="sxs-lookup"><span data-stu-id="adc53-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adc53-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="adc53-111">S_OK</span></span>|<span data-ttu-id="adc53-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="adc53-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="adc53-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="adc53-113">E_POINTER</span></span>|<span data-ttu-id="adc53-114">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="adc53-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adc53-115">需求</span><span class="sxs-lookup"><span data-stu-id="adc53-115">Requirements</span></span>  

 <span data-ttu-id="adc53-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="adc53-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc53-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="adc53-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="adc53-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="adc53-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adc53-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc53-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc53-120">See also</span></span>

- [<span data-ttu-id="adc53-121">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="adc53-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="adc53-122">裝載</span><span class="sxs-lookup"><span data-stu-id="adc53-122">Hosting</span></span>](index.md)
