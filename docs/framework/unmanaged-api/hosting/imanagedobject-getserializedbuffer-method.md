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
ms.openlocfilehash: 159ece09ae0b6a67780639da8aae8c0e4b412bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730685"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="3bcdf-102">IManagedObject::GetSerializedBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="3bcdf-102">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="3bcdf-103">取得此 managed 物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="3bcdf-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bcdf-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bcdf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bcdf-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bcdf-105">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="3bcdf-106">擴展字串的指標，該字串為已序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="3bcdf-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bcdf-107">備註</span><span class="sxs-lookup"><span data-stu-id="3bcdf-107">Remarks</span></span>  

 <span data-ttu-id="3bcdf-108">方法會將物件序列化， `GetSerializedBuffer` 以便將其封送處理至用戶端。</span><span class="sxs-lookup"><span data-stu-id="3bcdf-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bcdf-109">需求</span><span class="sxs-lookup"><span data-stu-id="3bcdf-109">Requirements</span></span>  

 <span data-ttu-id="3bcdf-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcdf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bcdf-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3bcdf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bcdf-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3bcdf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bcdf-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bcdf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcdf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bcdf-114">See also</span></span>

- [<span data-ttu-id="3bcdf-115">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="3bcdf-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
