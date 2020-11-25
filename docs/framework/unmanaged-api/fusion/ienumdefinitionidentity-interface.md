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
ms.openlocfilehash: f3872a2b03d3b22d695af1c104e9ae8ba8856990
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729001"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="1f233-102">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1f233-102">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="1f233-103">作為物件集合的列舉值 `IDefinitionIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="1f233-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f233-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f233-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1f233-105">方法</span><span class="sxs-lookup"><span data-stu-id="1f233-105">Methods</span></span>  
  
|<span data-ttu-id="1f233-106">方法</span><span class="sxs-lookup"><span data-stu-id="1f233-106">Method</span></span>|<span data-ttu-id="1f233-107">描述</span><span class="sxs-lookup"><span data-stu-id="1f233-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="1f233-108">取得新物件的介面指標 `IEnumDefinitionIdentity` ，該物件包含與這個相同的成員 `IEnumDefinitionIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="1f233-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="1f233-109">`IDefinitionIdentity`從目前位置開始取得指定數目的物件。</span><span class="sxs-lookup"><span data-stu-id="1f233-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="1f233-110">將指令指標移至這個的開頭 `IEnumDefinitionIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="1f233-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="1f233-111">從目前位置開始，將指令指標向下移動指定數目的元素。</span><span class="sxs-lookup"><span data-stu-id="1f233-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f233-112">需求</span><span class="sxs-lookup"><span data-stu-id="1f233-112">Requirements</span></span>  

 <span data-ttu-id="1f233-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f233-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f233-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="1f233-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1f233-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f233-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f233-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f233-116">See also</span></span>

- [<span data-ttu-id="1f233-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="1f233-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1f233-118">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1f233-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
