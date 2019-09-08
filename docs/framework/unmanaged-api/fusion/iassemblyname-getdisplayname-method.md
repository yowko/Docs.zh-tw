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
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796660"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="a0594-102">IAssemblyName::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="a0594-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="a0594-103">取得這個[IAssemblyName](iassemblyname-interface.md)物件所參考之元件的人類可讀名稱。</span><span class="sxs-lookup"><span data-stu-id="a0594-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0594-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0594-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0594-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0594-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="a0594-106">脫銷包含所參考元件名稱的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a0594-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="a0594-107">[in、out]`szDisplayName`以寬字元為單位的大小，包括 null 結束字元字元。</span><span class="sxs-lookup"><span data-stu-id="a0594-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="a0594-108">在[ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md)值的位元組合，會影響的功能`szDisplayName`。</span><span class="sxs-lookup"><span data-stu-id="a0594-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0594-109">需求</span><span class="sxs-lookup"><span data-stu-id="a0594-109">Requirements</span></span>  
 <span data-ttu-id="a0594-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0594-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0594-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="a0594-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a0594-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0594-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0594-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0594-113">See also</span></span>

- [<span data-ttu-id="a0594-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="a0594-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="a0594-115">融合列舉</span><span class="sxs-lookup"><span data-stu-id="a0594-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
