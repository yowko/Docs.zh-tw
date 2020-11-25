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
ms.openlocfilehash: 8020db491c3b66be38a9f6cbcb7551721859dcd5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723112"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="988e9-102">ICLRRuntimeInfo::SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="988e9-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>

<span data-ttu-id="988e9-103">設定將用來啟動執行時間的啟動旗標和主機設定檔案。</span><span class="sxs-lookup"><span data-stu-id="988e9-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="988e9-104">這個方法會取代 `startupFlags` [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 和 [CorBindToRuntimeHost](corbindtoruntimehost-function.md) 函數中的參數使用。</span><span class="sxs-lookup"><span data-stu-id="988e9-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="988e9-105">語法</span><span class="sxs-lookup"><span data-stu-id="988e9-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="988e9-106">參數</span><span class="sxs-lookup"><span data-stu-id="988e9-106">Parameters</span></span>  

 `dwStartupFlags`  
 <span data-ttu-id="988e9-107">在要設定的主機啟動旗標。</span><span class="sxs-lookup"><span data-stu-id="988e9-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="988e9-108">使用與 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 和 [CorBindToRuntimeHost](corbindtoruntimehost-function.md) 函數相同的旗標。</span><span class="sxs-lookup"><span data-stu-id="988e9-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="988e9-109">在要設定之主機設定檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="988e9-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="988e9-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="988e9-110">Return Value</span></span>  

 <span data-ttu-id="988e9-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="988e9-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="988e9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="988e9-112">HRESULT</span></span>|<span data-ttu-id="988e9-113">描述</span><span class="sxs-lookup"><span data-stu-id="988e9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="988e9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="988e9-114">S_OK</span></span>|<span data-ttu-id="988e9-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="988e9-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="988e9-116">備註</span><span class="sxs-lookup"><span data-stu-id="988e9-116">Remarks</span></span>  

 <span data-ttu-id="988e9-117">多執行緒主機應該同步處理對這個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="988e9-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="988e9-118">否則，執行緒 A 可能會 `SetStartupFlags` 線上程 b 完成的呼叫 `SetStartupFlags` ，以及執行緒 b 啟動執行時間之前呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="988e9-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="988e9-119">需求</span><span class="sxs-lookup"><span data-stu-id="988e9-119">Requirements</span></span>  

 <span data-ttu-id="988e9-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="988e9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="988e9-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="988e9-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="988e9-122">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="988e9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="988e9-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="988e9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988e9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="988e9-124">See also</span></span>

- [<span data-ttu-id="988e9-125">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="988e9-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="988e9-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="988e9-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="988e9-127">裝載</span><span class="sxs-lookup"><span data-stu-id="988e9-127">Hosting</span></span>](index.md)
