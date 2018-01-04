---
title: "METAHOST_CONFIG_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_CONFIG_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_CONFIG_FLAGS
helpviewer_keywords: METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5743356cdb2a99c4c5eb0c958bc5ca0815146d4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="21c8b-102">METAHOST_CONFIG_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="21c8b-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="21c8b-103">描述可能的旗標中傳回`pdwConfigFlags`參數[iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，指出是否存在與設定`useLegacyV2RuntimeActivationPolicy`屬性[ \<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔。</span><span class="sxs-lookup"><span data-stu-id="21c8b-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="21c8b-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="21c8b-105">成員</span><span class="sxs-lookup"><span data-stu-id="21c8b-105">Members</span></span>  
  
|<span data-ttu-id="21c8b-106">成員</span><span class="sxs-lookup"><span data-stu-id="21c8b-106">Member</span></span>|<span data-ttu-id="21c8b-107">描述</span><span class="sxs-lookup"><span data-stu-id="21c8b-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="21c8b-108">`useLegacyV2RuntimeActivationPolicy`屬性不存在於[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)。</span><span class="sxs-lookup"><span data-stu-id="21c8b-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="21c8b-109">`useLegacyV2RuntimeActivationPolicy`屬性已存在且設定至`true`。</span><span class="sxs-lookup"><span data-stu-id="21c8b-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="21c8b-110">`useLegacyV2RuntimeActivationPolicy`屬性已存在且設定至`false`。</span><span class="sxs-lookup"><span data-stu-id="21c8b-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="21c8b-111">在傳回的值會套用這個遮罩`pdwConfigFlags`以取得的值與`useLegacyV2RuntimeActivationPolicy`。</span><span class="sxs-lookup"><span data-stu-id="21c8b-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21c8b-112">備註</span><span class="sxs-lookup"><span data-stu-id="21c8b-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21c8b-113">需求</span><span class="sxs-lookup"><span data-stu-id="21c8b-113">Requirements</span></span>  
 <span data-ttu-id="21c8b-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21c8b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c8b-115">**標頭：** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="21c8b-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="21c8b-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="21c8b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21c8b-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21c8b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c8b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="21c8b-118">See Also</span></span>  
 [<span data-ttu-id="21c8b-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="21c8b-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="21c8b-120">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="21c8b-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="21c8b-121">\<啟動 > 項目</span><span class="sxs-lookup"><span data-stu-id="21c8b-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
