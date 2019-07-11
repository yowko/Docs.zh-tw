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
ms.openlocfilehash: f1fc128d15c56981f4bc6122e38e0514d006e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768616"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="8a478-102">IAssemblyName::IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="8a478-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="8a478-103">判斷指定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件是否等於這個`IAssemblyName`，根據指定的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="8a478-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a478-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a478-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a478-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a478-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="8a478-106">[in]`IAssemblyName`物件所要比較這`IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="8a478-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="8a478-107">[in]位元組合[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)影響比較的值。</span><span class="sxs-lookup"><span data-stu-id="8a478-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a478-108">需求</span><span class="sxs-lookup"><span data-stu-id="8a478-108">Requirements</span></span>  
 <span data-ttu-id="8a478-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a478-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a478-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8a478-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8a478-111">**NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a478-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a478-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a478-112">See also</span></span>

- [<span data-ttu-id="8a478-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="8a478-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="8a478-114">融合列舉</span><span class="sxs-lookup"><span data-stu-id="8a478-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
