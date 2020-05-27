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
ms.openlocfilehash: bb40ed65a2e34f1bf293e4c4c842d7db63d2eaa5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008439"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="f910c-102">METAHOST_POLICY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="f910c-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="f910c-103">提供大部分執行時間主機通用的系結原則。</span><span class="sxs-lookup"><span data-stu-id="f910c-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="f910c-104">[ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)方法會使用這個列舉。</span><span class="sxs-lookup"><span data-stu-id="f910c-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f910c-105">語法</span><span class="sxs-lookup"><span data-stu-id="f910c-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="f910c-106">成員</span><span class="sxs-lookup"><span data-stu-id="f910c-106">Members</span></span>  
  
|<span data-ttu-id="f910c-107">成員</span><span class="sxs-lookup"><span data-stu-id="f910c-107">Member</span></span>|<span data-ttu-id="f910c-108">描述</span><span class="sxs-lookup"><span data-stu-id="f910c-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="f910c-109">定義高相容性原則，這不會考慮任何載入目前進程中的 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="f910c-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="f910c-110">相反地，它只會考慮已安裝的 CLRs 和元件的喜好設定，衍生自元件檔本身、宣告的內建版本或設定檔。</span><span class="sxs-lookup"><span data-stu-id="f910c-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="f910c-111">根據 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft 的內容，在找不到完全相符的情況下，將升級原則套用至版本系結結果 \\ 。NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="f910c-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="f910c-112">這與[RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)的效果相同。</span><span class="sxs-lookup"><span data-stu-id="f910c-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="f910c-113">會傳回系結結果，就像提供給呼叫的影像是在新進程中啟動一樣。</span><span class="sxs-lookup"><span data-stu-id="f910c-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="f910c-114">目前，會 `GetRequestedRuntime` 忽略一組可載入的執行時間，並針對一組已安裝的執行時間進行系結。</span><span class="sxs-lookup"><span data-stu-id="f910c-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="f910c-115">此旗標可讓主機判斷 EXE 在啟動時將系結至哪個執行時間。</span><span class="sxs-lookup"><span data-stu-id="f910c-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="f910c-116">如果找不 `GetRequestedRuntime` 到與輸入參數相容的執行時間，就會顯示錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f910c-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="f910c-117">從 .NET Framework 4.5 開始，這個錯誤對話方塊可能會採用 Windows 功能對話方塊的形式，詢問使用者是否要啟用適當的功能。</span><span class="sxs-lookup"><span data-stu-id="f910c-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="f910c-118">`GetRequestedRuntime`會使用處理程式映射（以及任何對應的設定檔）做為系結程式的額外輸入。</span><span class="sxs-lookup"><span data-stu-id="f910c-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="f910c-119">根據預設， `GetRequestedRuntime` 在決定要系結的執行時間時，不會切換回進程影像路徑（通常是用來啟動進程的 EXE）。</span><span class="sxs-lookup"><span data-stu-id="f910c-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="f910c-120">`GetRequestedRuntime`當設定檔中沒有可用的資訊時，必須檢查是否已安裝適當的 SKU。</span><span class="sxs-lookup"><span data-stu-id="f910c-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="f910c-121">這可讓沒有設定檔的應用程式在較小的 Sku 上正常地失敗，而不是 .NET Framework 的預設安裝。</span><span class="sxs-lookup"><span data-stu-id="f910c-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="f910c-122">根據預設， `GetRequestedRuntime` 除非在設定檔元素中指定了 sku 屬性，否則不會檢查是否已安裝適當的 sku `<supportedRuntime />` 。</span><span class="sxs-lookup"><span data-stu-id="f910c-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="f910c-123">`GetRequestedRuntime`應該忽略 SEM_FAILCRITICALERRORS （藉由呼叫[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)函數來設定），並顯示 [錯誤] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f910c-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="f910c-124">根據預設，SEM_FAILCRITICALERRORS 會隱藏 [錯誤] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f910c-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="f910c-125">它可能已繼承自另一個進程，而在您的案例中可能不需要無訊息錯誤。</span><span class="sxs-lookup"><span data-stu-id="f910c-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f910c-126">備註</span><span class="sxs-lookup"><span data-stu-id="f910c-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f910c-127">需求</span><span class="sxs-lookup"><span data-stu-id="f910c-127">Requirements</span></span>  
 <span data-ttu-id="f910c-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f910c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f910c-129">**標頭：** Metahost。h</span><span class="sxs-lookup"><span data-stu-id="f910c-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="f910c-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f910c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f910c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f910c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f910c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f910c-132">See also</span></span>

- [<span data-ttu-id="f910c-133">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="f910c-133">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="f910c-134">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="f910c-134">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
