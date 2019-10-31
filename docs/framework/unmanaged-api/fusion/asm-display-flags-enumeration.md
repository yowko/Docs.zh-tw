---
title: ASM_DISPLAY_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
ms.openlocfilehash: a34648bece3b14d6175168f45916ca04aeeef71d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109249"
---
# <a name="asm_display_flags-enumeration"></a><span data-ttu-id="42a73-102">ASM_DISPLAY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="42a73-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="42a73-103">表示[IAssemblyName：： GetDisplayName](iassemblyname-getdisplayname-method.md)方法將抓取其顯示名稱之元件的版本、組建、文化特性、簽章等。</span><span class="sxs-lookup"><span data-stu-id="42a73-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42a73-104">語法</span><span class="sxs-lookup"><span data-stu-id="42a73-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =   
                      ASM_DISPLAYF_VERSION           |   
                      ASM_DISPLAYF_CULTURE           |   
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |   
                      ASM_DISPLAYF_RETARGET          |   
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="42a73-105">備註</span><span class="sxs-lookup"><span data-stu-id="42a73-105">Remarks</span></span>  
 <span data-ttu-id="42a73-106">`ASM_DISPLAYF_FULL` 反映對[IAssemblyName](iassemblyname-interface.md)物件版本所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="42a73-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](iassemblyname-interface.md) object.</span></span> <span data-ttu-id="42a73-107">請不要假設傳回的值是不可變的。</span><span class="sxs-lookup"><span data-stu-id="42a73-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42a73-108">需求</span><span class="sxs-lookup"><span data-stu-id="42a73-108">Requirements</span></span>  
 <span data-ttu-id="42a73-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42a73-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42a73-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="42a73-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="42a73-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42a73-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42a73-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42a73-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a73-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="42a73-113">See also</span></span>

- [<span data-ttu-id="42a73-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="42a73-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="42a73-115">融合列舉</span><span class="sxs-lookup"><span data-stu-id="42a73-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
