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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e322f5c7119d13c8a872bd87d00c1e55324b581
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135768"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="463be-102">METAHOST_CONFIG_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="463be-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="463be-103">描述可能的旗標傳入`pdwConfigFlags`的參數[iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，指出是否存在，並設定`useLegacyV2RuntimeActivationPolicy`屬性中[ \<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔。</span><span class="sxs-lookup"><span data-stu-id="463be-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463be-104">語法</span><span class="sxs-lookup"><span data-stu-id="463be-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="463be-105">成員</span><span class="sxs-lookup"><span data-stu-id="463be-105">Members</span></span>  
  
|<span data-ttu-id="463be-106">成員</span><span class="sxs-lookup"><span data-stu-id="463be-106">Member</span></span>|<span data-ttu-id="463be-107">描述</span><span class="sxs-lookup"><span data-stu-id="463be-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="463be-108">`useLegacyV2RuntimeActivationPolicy`屬性不存在於[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)。</span><span class="sxs-lookup"><span data-stu-id="463be-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="463be-109">`useLegacyV2RuntimeActivationPolicy`屬性已存在且設到`true`。</span><span class="sxs-lookup"><span data-stu-id="463be-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="463be-110">`useLegacyV2RuntimeActivationPolicy`屬性已存在且設到`false`。</span><span class="sxs-lookup"><span data-stu-id="463be-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="463be-111">在傳回的值套用這個遮罩`pdwConfigFlags`若要取得這些值`useLegacyV2RuntimeActivationPolicy`。</span><span class="sxs-lookup"><span data-stu-id="463be-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="463be-112">備註</span><span class="sxs-lookup"><span data-stu-id="463be-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="463be-113">需求</span><span class="sxs-lookup"><span data-stu-id="463be-113">Requirements</span></span>  
 <span data-ttu-id="463be-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="463be-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="463be-115">**標頭：** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="463be-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="463be-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="463be-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="463be-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="463be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463be-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="463be-118">See also</span></span>

- [<span data-ttu-id="463be-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="463be-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="463be-120">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="463be-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="463be-121">\<startup> 項目</span><span class="sxs-lookup"><span data-stu-id="463be-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
