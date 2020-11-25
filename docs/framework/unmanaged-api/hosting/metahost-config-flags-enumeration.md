---
title: METAHOST_CONFIG_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 01e55659bf2a348ec763f51112cbdcd706f27c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730002"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="bc036-102">METAHOST_CONFIG_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="bc036-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="bc036-103">描述在 `pdwConfigFlags` [ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)方法的參數中傳回的可能旗標，指出 `useLegacyV2RuntimeActivationPolicy` 設定檔[ \<startup> 元素](../../configure-apps/file-schema/startup/startup-element.md)中屬性的存在和設定。</span><span class="sxs-lookup"><span data-stu-id="bc036-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc036-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc036-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="bc036-105">成員</span><span class="sxs-lookup"><span data-stu-id="bc036-105">Members</span></span>  
  
|<span data-ttu-id="bc036-106">member</span><span class="sxs-lookup"><span data-stu-id="bc036-106">Member</span></span>|<span data-ttu-id="bc036-107">描述</span><span class="sxs-lookup"><span data-stu-id="bc036-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="bc036-108">`useLegacyV2RuntimeActivationPolicy`屬性不存在於[ \<startup> 元素](../../configure-apps/file-schema/startup/startup-element.md)中。</span><span class="sxs-lookup"><span data-stu-id="bc036-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="bc036-109">`useLegacyV2RuntimeActivationPolicy`屬性存在並設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="bc036-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="bc036-110">`useLegacyV2RuntimeActivationPolicy`屬性存在並設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="bc036-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="bc036-111">將這個遮罩套用至傳回的值， `pdwConfigFlags` 以取得與相關的值 `useLegacyV2RuntimeActivationPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="bc036-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc036-112">備註</span><span class="sxs-lookup"><span data-stu-id="bc036-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc036-113">需求</span><span class="sxs-lookup"><span data-stu-id="bc036-113">Requirements</span></span>  

 <span data-ttu-id="bc036-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc036-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc036-115">**標頭：** Metahost。h</span><span class="sxs-lookup"><span data-stu-id="bc036-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="bc036-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bc036-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc036-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc036-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc036-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc036-118">See also</span></span>

- [<span data-ttu-id="bc036-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="bc036-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="bc036-120">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="bc036-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="bc036-121">\<startup> 元素</span><span class="sxs-lookup"><span data-stu-id="bc036-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
