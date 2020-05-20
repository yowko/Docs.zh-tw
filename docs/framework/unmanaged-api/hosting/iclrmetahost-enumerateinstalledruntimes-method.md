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
ms.openlocfilehash: c99607bfe5fda01eb1abfd7771cb3907ddabeec5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703784"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="08993-102">ICLRMetaHost::EnumerateInstalledRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="08993-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="08993-103">傳回列舉，其中包含電腦上所安裝之每個 common language runtime （CLR）版本的有效[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="08993-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08993-104">語法</span><span class="sxs-lookup"><span data-stu-id="08993-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08993-105">參數</span><span class="sxs-lookup"><span data-stu-id="08993-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="08993-106">脫銷對應至電腦上所安裝之每個 CLR 版本的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面列舉。</span><span class="sxs-lookup"><span data-stu-id="08993-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08993-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="08993-107">Return Value</span></span>  
 <span data-ttu-id="08993-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="08993-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="08993-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08993-109">HRESULT</span></span>|<span data-ttu-id="08993-110">說明</span><span class="sxs-lookup"><span data-stu-id="08993-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08993-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="08993-111">S_OK</span></span>|<span data-ttu-id="08993-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="08993-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="08993-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="08993-113">E_POINTER</span></span>|<span data-ttu-id="08993-114">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="08993-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08993-115">需求</span><span class="sxs-lookup"><span data-stu-id="08993-115">Requirements</span></span>  
 <span data-ttu-id="08993-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08993-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08993-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="08993-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08993-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08993-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08993-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08993-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08993-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08993-120">See also</span></span>

- [<span data-ttu-id="08993-121">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="08993-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="08993-122">裝載</span><span class="sxs-lookup"><span data-stu-id="08993-122">Hosting</span></span>](index.md)
