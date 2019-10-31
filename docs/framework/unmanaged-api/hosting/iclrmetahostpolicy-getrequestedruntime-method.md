---
title: ICLRMetaHostPolicy::GetRequestedRuntime 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 1b07029990ef529ded57bc569beff1061ad0f938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140876"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="39b18-102">ICLRMetaHostPolicy::GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="39b18-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="39b18-103">提供 Common Language Runtime (CLR) 慣用版本的介面，這是根據裝載原則、Managed 組件、版本字串和組態資料流。</span><span class="sxs-lookup"><span data-stu-id="39b18-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="39b18-104">這個方法實際上並不會載入或啟動 CLR，而只會傳回代表原則結果的[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="39b18-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="39b18-105">這個方法會取代[GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)、 [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)、 [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)、 [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)和[GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)方法。</span><span class="sxs-lookup"><span data-stu-id="39b18-105">This method supersedes the [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="39b18-106">語法</span><span class="sxs-lookup"><span data-stu-id="39b18-106">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="39b18-107">參數</span><span class="sxs-lookup"><span data-stu-id="39b18-107">Parameters</span></span>

|<span data-ttu-id="39b18-108">[屬性]</span><span class="sxs-lookup"><span data-stu-id="39b18-108">Name</span></span>|<span data-ttu-id="39b18-109">描述</span><span class="sxs-lookup"><span data-stu-id="39b18-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="39b18-110">[in] 必要項。</span><span class="sxs-lookup"><span data-stu-id="39b18-110">[in] Required.</span></span> <span data-ttu-id="39b18-111">指定[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列舉的成員，代表系結原則，以及任何數目的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="39b18-111">Specifies a member of the [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="39b18-112">目前唯一可用的原則是[METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="39b18-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="39b18-113">修飾詞包括[METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)和[METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="39b18-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="39b18-114">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-114">[in] Optional.</span></span> <span data-ttu-id="39b18-115">指定組件檔路徑。</span><span class="sxs-lookup"><span data-stu-id="39b18-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="39b18-116">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-116">[in] Optional.</span></span> <span data-ttu-id="39b18-117">以 <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> 指定組態檔。</span><span class="sxs-lookup"><span data-stu-id="39b18-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="39b18-118">[in, out] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-118">[in, out] Optional.</span></span> <span data-ttu-id="39b18-119">指定或傳回要載入的慣用 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="39b18-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="39b18-120">[in, out] 必要項。</span><span class="sxs-lookup"><span data-stu-id="39b18-120">[in, out] Required.</span></span> <span data-ttu-id="39b18-121">指定 `pwzVersion` 做為輸入的預期大小，以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="39b18-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="39b18-122">如果 `pwzVersion` 為 null，`pcchVersion` 包含 `GetRequestedRuntime` 傳回時 `pwzVersion` 的預期大小，以便預先配置，否則 `pcchVersion` 包含要寫入 `pwzVersion` 的字元數目。</span><span class="sxs-lookup"><span data-stu-id="39b18-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="39b18-123">[out] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-123">[out] Optional.</span></span> <span data-ttu-id="39b18-124">當 `GetRequestedRuntime` 傳回時，會包含對應至所傳回之[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="39b18-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="39b18-125">[in, out] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-125">[in, out] Optional.</span></span> <span data-ttu-id="39b18-126">指定 `pwzImageVersion` 做為輸入的大小，以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="39b18-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="39b18-127">如果 `pwzImageVersion` 為 null， `pcchImageVersion` 包含 `GetRequestedRuntime` 傳回時的 `pwzImageVersion` 必要大小，以便預先配置。</span><span class="sxs-lookup"><span data-stu-id="39b18-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="39b18-128">[out] 選用。</span><span class="sxs-lookup"><span data-stu-id="39b18-128">[out] Optional.</span></span> <span data-ttu-id="39b18-129">如果 `GetRequestedRuntime` 在系結程式期間使用設定檔，當它傳回時，`pdwConfigFlags` 會包含[METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md)值，指出[\<啟動 >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)專案是否已設定 `useLegacyV2RuntimeActivationPolicy` 屬性，而值為屬性。</span><span class="sxs-lookup"><span data-stu-id="39b18-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="39b18-130">將[METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTI加值稅ION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) MASK 套用至 `pdwConfigFlags`，以取得與 `useLegacyV2RuntimeActivationPolicy`相關的值。</span><span class="sxs-lookup"><span data-stu-id="39b18-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="39b18-131">在指定所要求之[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的介面識別碼 IID_ICLRRuntimeInfo。</span><span class="sxs-lookup"><span data-stu-id="39b18-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="39b18-132">脫銷當 `GetRequestedRuntime` 傳回時，會包含對應[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="39b18-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="39b18-133">備註</span><span class="sxs-lookup"><span data-stu-id="39b18-133">Remarks</span></span>

<span data-ttu-id="39b18-134">當這個方法成功時，它的副作用是會合併其他旗標與傳回之執行階段介面的目前預設啟動旗標，並且只在 `<configuration><runtime>` 區段內有一或多個下列項目存在於組態資料流時：</span><span class="sxs-lookup"><span data-stu-id="39b18-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="39b18-135">`<gcServer enabled="true"/>` 會導致設定 `STARTUP_SERVER_GC`。</span><span class="sxs-lookup"><span data-stu-id="39b18-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="39b18-136">`<etwEnable enabled="true"/>` 會導致設定 `STARTUP_ETW`。</span><span class="sxs-lookup"><span data-stu-id="39b18-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="39b18-137">`<appDomainResourceMonitoring enabled="true"/>` 會導致設定 `STARTUP_ARM`。</span><span class="sxs-lookup"><span data-stu-id="39b18-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="39b18-138">產生的預設 `STARTUP_FLAGS` 值是從上述清單設定之值與預設啟動旗標值的位元 OR 合併。</span><span class="sxs-lookup"><span data-stu-id="39b18-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="39b18-139">傳回值</span><span class="sxs-lookup"><span data-stu-id="39b18-139">Return Value</span></span>

<span data-ttu-id="39b18-140">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="39b18-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="39b18-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39b18-141">HRESULT</span></span>|<span data-ttu-id="39b18-142">描述</span><span class="sxs-lookup"><span data-stu-id="39b18-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="39b18-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="39b18-143">S_OK</span></span>|<span data-ttu-id="39b18-144">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="39b18-144">The method completed successfully.</span></span>|
|<span data-ttu-id="39b18-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="39b18-145">E_POINTER</span></span>|<span data-ttu-id="39b18-146">`pwzVersion` 不是 null 且 `pcchVersion` 是 null。</span><span class="sxs-lookup"><span data-stu-id="39b18-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="39b18-147">-或-</span><span class="sxs-lookup"><span data-stu-id="39b18-147">-or-</span></span><br /><br /> <span data-ttu-id="39b18-148">`pwzImageVersion` 不是 null 且 `pcchImageVersion` 是 null。</span><span class="sxs-lookup"><span data-stu-id="39b18-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="39b18-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="39b18-149">E_INVALIDARG</span></span>|<span data-ttu-id="39b18-150">`dwPolicyFlags` 未指定 `METAHOST_POLICY_HIGHCOMPAT`。</span><span class="sxs-lookup"><span data-stu-id="39b18-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="39b18-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="39b18-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="39b18-152">配置給 `pwzVersion` 的記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="39b18-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="39b18-153">-或-</span><span class="sxs-lookup"><span data-stu-id="39b18-153">-or-</span></span><br /><br /> <span data-ttu-id="39b18-154">配置給 `pwzImageVersion` 的記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="39b18-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="39b18-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="39b18-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="39b18-156">`dwPolicyFlags` 包括 METAHOST_POLICY_APPLY_UPGRADE_POLICY，且 `pwzVersion` 和 `pcchVersion` 都是 null。</span><span class="sxs-lookup"><span data-stu-id="39b18-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="39b18-157">需求</span><span class="sxs-lookup"><span data-stu-id="39b18-157">Requirements</span></span>

<span data-ttu-id="39b18-158">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39b18-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="39b18-159">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="39b18-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="39b18-160">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="39b18-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="39b18-161">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39b18-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="39b18-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="39b18-162">See also</span></span>

- [<span data-ttu-id="39b18-163">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="39b18-163">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="39b18-164">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="39b18-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="39b18-165">裝載介面</span><span class="sxs-lookup"><span data-stu-id="39b18-165">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="39b18-166">裝載</span><span class="sxs-lookup"><span data-stu-id="39b18-166">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
