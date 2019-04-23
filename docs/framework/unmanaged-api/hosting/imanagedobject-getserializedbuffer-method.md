---
title: IManagedObject::GetSerializedBuffer 方法
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb9242160b684b3c7b90756d7b20811ad162fc30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156139"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="d488c-102">IManagedObject::GetSerializedBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="d488c-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="d488c-103">取得此受管理物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="d488c-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d488c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d488c-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d488c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d488c-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="d488c-106">[out]序列化的物件的字串指標。</span><span class="sxs-lookup"><span data-stu-id="d488c-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d488c-107">備註</span><span class="sxs-lookup"><span data-stu-id="d488c-107">Remarks</span></span>  
 <span data-ttu-id="d488c-108">`GetSerializedBuffer`方法序列化的物件，因此它可以封送處理至用戶端。</span><span class="sxs-lookup"><span data-stu-id="d488c-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d488c-109">需求</span><span class="sxs-lookup"><span data-stu-id="d488c-109">Requirements</span></span>  
 <span data-ttu-id="d488c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d488c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d488c-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d488c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d488c-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d488c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d488c-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d488c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d488c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d488c-114">See also</span></span>

- [<span data-ttu-id="d488c-115">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="d488c-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
