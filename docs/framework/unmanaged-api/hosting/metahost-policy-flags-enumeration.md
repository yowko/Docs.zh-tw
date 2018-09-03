---
title: METAHOST_POLICY_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a96af0c66d85c7eec9a97be3ba8c756b1e91849
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486671"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="9aa97-102">METAHOST_POLICY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="9aa97-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="9aa97-103">提供通用於大多數的執行階段主機的繫結原則。</span><span class="sxs-lookup"><span data-stu-id="9aa97-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="9aa97-104">這個列舉型別由[iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9aa97-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa97-105">語法</span><span class="sxs-lookup"><span data-stu-id="9aa97-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="9aa97-106">成員</span><span class="sxs-lookup"><span data-stu-id="9aa97-106">Members</span></span>  
  
|<span data-ttu-id="9aa97-107">成員</span><span class="sxs-lookup"><span data-stu-id="9aa97-107">Member</span></span>|<span data-ttu-id="9aa97-108">描述</span><span class="sxs-lookup"><span data-stu-id="9aa97-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="9aa97-109">定義設定高相容性原則，它不會考慮任何 common language runtime (CLR) 載入到目前的處理序。</span><span class="sxs-lookup"><span data-stu-id="9aa97-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="9aa97-110">相反地，它會視為已安裝的 CLRs 和喜好設定的元件，為衍生自組件檔案本身、 宣告建置針對版本或組態檔。</span><span class="sxs-lookup"><span data-stu-id="9aa97-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="9aa97-111">當適用於升級的原則版本繫結結果完全符合找不到，根據 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft 內容\\。NETFramework\Policy\Upgrades。</span><span class="sxs-lookup"><span data-stu-id="9aa97-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="9aa97-112">這有相同的效果[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa97-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="9aa97-113">如同呼叫提供的映像所啟動的新處理序中，會傳回繫結結果。</span><span class="sxs-lookup"><span data-stu-id="9aa97-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="9aa97-114">目前，`GetRequestedRuntime`會略過的可載入的執行階段設定，並針對已安裝執行階段組繫結。</span><span class="sxs-lookup"><span data-stu-id="9aa97-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="9aa97-115">這個旗標可讓主應用程式判斷 EXE 會繫結至啟動時執行階段。</span><span class="sxs-lookup"><span data-stu-id="9aa97-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="9aa97-116">如果顯示錯誤對話方塊`GetRequestedRuntime`是找不到適用於輸入參數的執行階段。</span><span class="sxs-lookup"><span data-stu-id="9aa97-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="9aa97-117">開頭為[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，此錯誤對話方塊中可採用的 Windows 功能 對話方塊，詢問使用者是否想要啟用適當的功能。</span><span class="sxs-lookup"><span data-stu-id="9aa97-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="9aa97-118">`GetRequestedRuntime` 做為繫結程序的其他輸入會使用處理序映像 （和任何對應的組態檔）。</span><span class="sxs-lookup"><span data-stu-id="9aa97-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="9aa97-119">根據預設，`GetRequestedRuntime`不會回到處理程序映像路徑 (通常用來啟動處理序 EXE) 來判斷要繫結至執行階段時。</span><span class="sxs-lookup"><span data-stu-id="9aa97-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="9aa97-120">`GetRequestedRuntime` 必須檢查組態檔中不未提供任何資訊時，是否已安裝適當的 SKU。</span><span class="sxs-lookup"><span data-stu-id="9aa97-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="9aa97-121">這可讓沒有組態檔，以較小的 Sku，比預設安裝的.NET framework 上執行正常失敗的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9aa97-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="9aa97-122">根據預設，`GetRequestedRuntime`不會檢查適當的 SKU 是否已安裝，除非在組態檔中指定的 SKU 屬性`<supportedRuntime />`項目。</span><span class="sxs-lookup"><span data-stu-id="9aa97-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="9aa97-123">`GetRequestedRuntime` 必須檢查組態檔中不未提供任何資訊時，是否已安裝適當的 SKU。</span><span class="sxs-lookup"><span data-stu-id="9aa97-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="9aa97-124">這可讓沒有組態檔，以較小的 Sku，比預設安裝的.NET framework 上執行正常失敗的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9aa97-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="9aa97-125">根據預設，`GetRequestedRuntime`不會檢查適當的 SKU 是否已安裝，除非在組態檔中指定的 SKU 屬性`<supportedRuntime />`項目。</span><span class="sxs-lookup"><span data-stu-id="9aa97-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="9aa97-126">`GetRequestedRuntime` 應忽略 SEM_FAILCRITICALERRORS (此值會設定藉由呼叫[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)函式)，並顯示錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9aa97-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="9aa97-127">根據預設，SEM_FAILCRITICALERRORS 隱藏錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9aa97-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="9aa97-128">它可能有已繼承自另一個處理序，並無訊息的錯誤可能不想要在您的案例。</span><span class="sxs-lookup"><span data-stu-id="9aa97-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aa97-129">備註</span><span class="sxs-lookup"><span data-stu-id="9aa97-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa97-130">需求</span><span class="sxs-lookup"><span data-stu-id="9aa97-130">Requirements</span></span>  
 <span data-ttu-id="9aa97-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa97-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa97-132">**標頭：** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="9aa97-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="9aa97-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9aa97-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aa97-134">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa97-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa97-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aa97-135">See Also</span></span>  
 [<span data-ttu-id="9aa97-136">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="9aa97-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="9aa97-137">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9aa97-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
