---
title: IAssemblyName::GetDisplayName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d8cbc540377c8f2a26b8fafef35c19e94a59c51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536005"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="4fef1-102">IAssemblyName::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="4fef1-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="4fef1-103">取得人類可讀名稱所參考的組件[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="4fef1-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fef1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fef1-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fef1-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fef1-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="4fef1-106">[out]包含參考的組件名稱的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4fef1-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="4fef1-107">[in、 out]大小`szDisplayName`寬字元，包括 null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="4fef1-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="4fef1-108">[in]位元組合[ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md)影響的功能值`szDisplayName`。</span><span class="sxs-lookup"><span data-stu-id="4fef1-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fef1-109">需求</span><span class="sxs-lookup"><span data-stu-id="4fef1-109">Requirements</span></span>  
 <span data-ttu-id="4fef1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fef1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fef1-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4fef1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4fef1-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fef1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fef1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fef1-113">See also</span></span>
- [<span data-ttu-id="4fef1-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="4fef1-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="4fef1-115">融合列舉</span><span class="sxs-lookup"><span data-stu-id="4fef1-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
