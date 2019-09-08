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
ms.openlocfilehash: 88c2513229b6a4183cadbdc78e505910e01e152c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796481"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="bdd2d-102">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="bdd2d-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="bdd2d-103">作為`IDefinitionIdentity`物件集合的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdd2d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="bdd2d-105">方法</span><span class="sxs-lookup"><span data-stu-id="bdd2d-105">Methods</span></span>  
  
|<span data-ttu-id="bdd2d-106">方法</span><span class="sxs-lookup"><span data-stu-id="bdd2d-106">Method</span></span>|<span data-ttu-id="bdd2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="bdd2d-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="bdd2d-108">取得新`IEnumDefinitionIdentity`物件的介面指標，其中包含與這個`IEnumDefinitionIdentity`相同的成員。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="bdd2d-109">取得指定數目的`IDefinitionIdentity`物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="bdd2d-110">將指令指標移至這個`IEnumDefinitionIdentity`的開頭。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="bdd2d-111">從目前位置開始，將指令指標向下移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdd2d-112">需求</span><span class="sxs-lookup"><span data-stu-id="bdd2d-112">Requirements</span></span>  
 <span data-ttu-id="bdd2d-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdd2d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd2d-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="bdd2d-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bdd2d-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd2d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdd2d-116">See also</span></span>

- [<span data-ttu-id="bdd2d-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="bdd2d-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="bdd2d-118">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="bdd2d-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
