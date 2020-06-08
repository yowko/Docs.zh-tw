---
title: ICLRRuntimeInfo::SetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504013"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="03bf8-102">ICLRRuntimeInfo::SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="03bf8-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="03bf8-103">設定將用來啟動執行時間的啟動旗標和主機設定檔。</span><span class="sxs-lookup"><span data-stu-id="03bf8-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="03bf8-104">這個方法會取代 `startupFlags` [CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函式中的參數使用。</span><span class="sxs-lookup"><span data-stu-id="03bf8-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bf8-105">語法</span><span class="sxs-lookup"><span data-stu-id="03bf8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03bf8-106">參數</span><span class="sxs-lookup"><span data-stu-id="03bf8-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="03bf8-107">在要設定的主機啟動旗標。</span><span class="sxs-lookup"><span data-stu-id="03bf8-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="03bf8-108">使用與[CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函數相同的旗標。</span><span class="sxs-lookup"><span data-stu-id="03bf8-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="03bf8-109">在要設定的主機設定檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="03bf8-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03bf8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="03bf8-110">Return Value</span></span>  
 <span data-ttu-id="03bf8-111">這個方法會傳回下列特定的 HRESULT，以及指出方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="03bf8-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="03bf8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03bf8-112">HRESULT</span></span>|<span data-ttu-id="03bf8-113">說明</span><span class="sxs-lookup"><span data-stu-id="03bf8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03bf8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="03bf8-114">S_OK</span></span>|<span data-ttu-id="03bf8-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="03bf8-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03bf8-116">備註</span><span class="sxs-lookup"><span data-stu-id="03bf8-116">Remarks</span></span>  
 <span data-ttu-id="03bf8-117">多執行緒主機應該同步處理這個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="03bf8-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="03bf8-118">否則，執行緒 A 可能會 `SetStartupFlags` 線上程 b 完成的呼叫之後 `SetStartupFlags` 和執行緒 b 啟動執行時間之前呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="03bf8-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03bf8-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="03bf8-119">Requirements</span></span>  
 <span data-ttu-id="03bf8-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03bf8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03bf8-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="03bf8-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03bf8-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03bf8-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03bf8-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03bf8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bf8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03bf8-124">See also</span></span>

- [<span data-ttu-id="03bf8-125">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="03bf8-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="03bf8-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="03bf8-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="03bf8-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="03bf8-127">Hosting</span></span>](index.md)
