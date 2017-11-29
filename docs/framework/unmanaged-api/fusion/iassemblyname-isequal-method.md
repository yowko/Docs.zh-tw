---
title: "IAssemblyName::IsEqual 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.IsEqual
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51a4fbe005a8e270b9fe6767ae5173bd027a191b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="c38bf-102">IAssemblyName::IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="c38bf-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="c38bf-103">決定指定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件是否等於此`IAssemblyName`，根據指定的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="c38bf-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c38bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="c38bf-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c38bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="c38bf-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="c38bf-106">[in]`IAssemblyName`物件要與這個比較`IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="c38bf-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="c38bf-107">[in]位元組合[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)影響比較的值。</span><span class="sxs-lookup"><span data-stu-id="c38bf-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c38bf-108">需求</span><span class="sxs-lookup"><span data-stu-id="c38bf-108">Requirements</span></span>  
 <span data-ttu-id="c38bf-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c38bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c38bf-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c38bf-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c38bf-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c38bf-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38bf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c38bf-112">See Also</span></span>  
 [<span data-ttu-id="c38bf-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="c38bf-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="c38bf-114">融合列舉</span><span class="sxs-lookup"><span data-stu-id="c38bf-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
