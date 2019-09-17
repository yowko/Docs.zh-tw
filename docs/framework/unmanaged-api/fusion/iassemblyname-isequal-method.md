---
title: IAssemblyName::IsEqual 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796565"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="95ac1-102">IAssemblyName::IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="95ac1-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="95ac1-103">根據指定的比較旗標，判斷指定的`IAssemblyName`[IAssemblyName](iassemblyname-interface.md) 物件是否等於這個。</span><span class="sxs-lookup"><span data-stu-id="95ac1-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="95ac1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95ac1-105">參數</span><span class="sxs-lookup"><span data-stu-id="95ac1-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="95ac1-106">在要`IAssemblyName`與之`IAssemblyName`比較的物件。</span><span class="sxs-lookup"><span data-stu-id="95ac1-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="95ac1-107">在影響比較之[ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md)值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="95ac1-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95ac1-108">需求</span><span class="sxs-lookup"><span data-stu-id="95ac1-108">Requirements</span></span>  
 <span data-ttu-id="95ac1-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95ac1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ac1-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="95ac1-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="95ac1-111">**.Net Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ac1-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ac1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95ac1-112">See also</span></span>

- [<span data-ttu-id="95ac1-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="95ac1-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="95ac1-114">融合列舉</span><span class="sxs-lookup"><span data-stu-id="95ac1-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
