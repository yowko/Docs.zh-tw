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
ms.openlocfilehash: ebaab57b647250823443b48d9e45921036372d5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176600"
---
# <a name="asm_display_flags-enumeration"></a><span data-ttu-id="16f65-102">ASM_DISPLAY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="16f65-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="16f65-103">指示程式集的版本、生成、區域性、簽名等，其顯示名稱將由[IAssemblyname：getDisplayName](iassemblyname-getdisplayname-method.md)方法檢索。</span><span class="sxs-lookup"><span data-stu-id="16f65-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f65-104">語法</span><span class="sxs-lookup"><span data-stu-id="16f65-104">Syntax</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="16f65-105">備註</span><span class="sxs-lookup"><span data-stu-id="16f65-105">Remarks</span></span>  
 <span data-ttu-id="16f65-106">`ASM_DISPLAYF_FULL`反映對[IAssemblyName](iassemblyname-interface.md)物件版本所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="16f65-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](iassemblyname-interface.md) object.</span></span> <span data-ttu-id="16f65-107">不要假定返回的值是不可變的。</span><span class="sxs-lookup"><span data-stu-id="16f65-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f65-108">需求</span><span class="sxs-lookup"><span data-stu-id="16f65-108">Requirements</span></span>  
 <span data-ttu-id="16f65-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16f65-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f65-110">**標題：** 融合.h</span><span class="sxs-lookup"><span data-stu-id="16f65-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="16f65-111">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="16f65-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16f65-112">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f65-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f65-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16f65-113">See also</span></span>

- [<span data-ttu-id="16f65-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="16f65-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="16f65-115">融合列舉</span><span class="sxs-lookup"><span data-stu-id="16f65-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
