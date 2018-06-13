---
title: IEnumDefinitionIdentity 介面
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34186ee8825c0981ec095cf855c76ff5f800907d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432350"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="e2304-102">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="e2304-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="e2304-103">做為集合的列舉值`IDefinitionIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="e2304-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2304-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2304-104">Syntax</span></span>  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e2304-105">方法</span><span class="sxs-lookup"><span data-stu-id="e2304-105">Methods</span></span>  
  
|<span data-ttu-id="e2304-106">方法</span><span class="sxs-lookup"><span data-stu-id="e2304-106">Method</span></span>|<span data-ttu-id="e2304-107">描述</span><span class="sxs-lookup"><span data-stu-id="e2304-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="e2304-108">取得新的介面指標`IEnumDefinitionIdentity`物件，其中包含這個相同的成員`IEnumDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2304-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="e2304-109">取得指定的數目`IDefinitionIdentity`物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e2304-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="e2304-110">將指令指標移到開頭`IEnumDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2304-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="e2304-111">將指令指標向前移以指定的項目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e2304-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2304-112">需求</span><span class="sxs-lookup"><span data-stu-id="e2304-112">Requirements</span></span>  
 <span data-ttu-id="e2304-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2304-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2304-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e2304-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e2304-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2304-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2304-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2304-116">See Also</span></span>  
 [<span data-ttu-id="e2304-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="e2304-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="e2304-118">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="e2304-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
