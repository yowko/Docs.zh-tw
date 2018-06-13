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
ms.openlocfilehash: 043394541f5ed91b85a57f4cb13c61cca442bfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431837"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="b7a87-102">IAssemblyName::IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="b7a87-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="b7a87-103">決定指定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件是否等於此`IAssemblyName`，根據指定的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="b7a87-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a87-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7a87-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7a87-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7a87-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b7a87-106">[in]`IAssemblyName`物件要與這個比較`IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="b7a87-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="b7a87-107">[in]位元組合[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)影響比較的值。</span><span class="sxs-lookup"><span data-stu-id="b7a87-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a87-108">需求</span><span class="sxs-lookup"><span data-stu-id="b7a87-108">Requirements</span></span>  
 <span data-ttu-id="b7a87-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a87-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a87-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b7a87-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b7a87-111">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a87-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a87-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7a87-112">See Also</span></span>  
 [<span data-ttu-id="b7a87-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="b7a87-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="b7a87-114">融合列舉</span><span class="sxs-lookup"><span data-stu-id="b7a87-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
