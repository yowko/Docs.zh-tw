---
title: IEnumReferenceIdentity 介面
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796439"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="f754c-102">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="f754c-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="f754c-103">作為物件集合的`IReferenceIdentity`列舉值。</span><span class="sxs-lookup"><span data-stu-id="f754c-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f754c-104">方法</span><span class="sxs-lookup"><span data-stu-id="f754c-104">Methods</span></span>  
  
|<span data-ttu-id="f754c-105">方法</span><span class="sxs-lookup"><span data-stu-id="f754c-105">Method</span></span>|<span data-ttu-id="f754c-106">說明</span><span class="sxs-lookup"><span data-stu-id="f754c-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="f754c-107">取得新`IEnumReferenceIdentity`的介面指標，其中包含與這個`IEnumReferenceIdentity`相同的成員。</span><span class="sxs-lookup"><span data-stu-id="f754c-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="f754c-108">取得指定數目的`IReferenceIdentity`物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="f754c-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="f754c-109">將指令指標移至這個`IEnumReferenceIdentity`的開頭。</span><span class="sxs-lookup"><span data-stu-id="f754c-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="f754c-110">從目前位置開始，將指令指標向下移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="f754c-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f754c-111">需求</span><span class="sxs-lookup"><span data-stu-id="f754c-111">Requirements</span></span>  
 <span data-ttu-id="f754c-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f754c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f754c-113">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="f754c-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f754c-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f754c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f754c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f754c-115">See also</span></span>

- [<span data-ttu-id="f754c-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="f754c-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="f754c-117">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="f754c-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
