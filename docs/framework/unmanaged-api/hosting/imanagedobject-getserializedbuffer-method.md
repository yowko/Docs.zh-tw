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
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842424"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="ae0cb-102">IManagedObject::GetSerializedBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="ae0cb-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="ae0cb-103">取得這個 managed 物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="ae0cb-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae0cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae0cb-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="ae0cb-106">脫銷序列化物件之字串的指標。</span><span class="sxs-lookup"><span data-stu-id="ae0cb-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae0cb-107">備註</span><span class="sxs-lookup"><span data-stu-id="ae0cb-107">Remarks</span></span>  
 <span data-ttu-id="ae0cb-108">方法會序列化 `GetSerializedBuffer` 物件，以便將其封送處理至用戶端。</span><span class="sxs-lookup"><span data-stu-id="ae0cb-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0cb-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="ae0cb-109">Requirements</span></span>  
 <span data-ttu-id="ae0cb-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae0cb-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ae0cb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae0cb-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ae0cb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae0cb-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae0cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0cb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae0cb-114">See also</span></span>

- [<span data-ttu-id="ae0cb-115">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="ae0cb-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
