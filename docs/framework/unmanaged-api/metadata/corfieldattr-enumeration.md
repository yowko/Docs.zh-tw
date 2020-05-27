---
title: CorFieldAttr 列舉
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: dea69e18fc517eddddc5b99950a6f3b16ee3e426
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007399"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="87b92-102">CorFieldAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="87b92-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="87b92-103">包含值，這些值描述與欄位有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="87b92-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b92-104">語法</span><span class="sxs-lookup"><span data-stu-id="87b92-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="87b92-105">成員</span><span class="sxs-lookup"><span data-stu-id="87b92-105">Members</span></span>  
  
|<span data-ttu-id="87b92-106">成員</span><span class="sxs-lookup"><span data-stu-id="87b92-106">Member</span></span>|<span data-ttu-id="87b92-107">描述</span><span class="sxs-lookup"><span data-stu-id="87b92-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="87b92-108">指定協助工具資訊。</span><span class="sxs-lookup"><span data-stu-id="87b92-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="87b92-109">指定無法參考此欄位。</span><span class="sxs-lookup"><span data-stu-id="87b92-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="87b92-110">指定欄位只能由其父類型存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="87b92-111">指定欄位可由其元件中的衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="87b92-112">指定欄位可由其元件中的所有類型存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="87b92-113">指定欄位只能由其類型和衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="87b92-114">指定欄位可由衍生類別以及其元件中的所有類型存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="87b92-115">指定此欄位可供具有此範圍可見度的所有類型存取。</span><span class="sxs-lookup"><span data-stu-id="87b92-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="87b92-116">指定欄位是其類型的成員，而不是實例成員。</span><span class="sxs-lookup"><span data-stu-id="87b92-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="87b92-117">指定欄位在初始化之後就無法變更。</span><span class="sxs-lookup"><span data-stu-id="87b92-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="87b92-118">指定域值是編譯時間常數。</span><span class="sxs-lookup"><span data-stu-id="87b92-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="87b92-119">指定當欄位的類型是遠端時，不會序列化該欄位。</span><span class="sxs-lookup"><span data-stu-id="87b92-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="87b92-120">指定欄位為 [特殊]，而其名稱描述了如何。</span><span class="sxs-lookup"><span data-stu-id="87b92-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="87b92-121">指定透過 PInvoke 轉送欄位執行。</span><span class="sxs-lookup"><span data-stu-id="87b92-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="87b92-122">保留供 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="87b92-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="87b92-123">指定 common language runtime 中繼資料內部 Api 應該檢查名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="87b92-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="87b92-124">指定欄位包含封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="87b92-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="87b92-125">指定此欄位含有預設值。</span><span class="sxs-lookup"><span data-stu-id="87b92-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="87b92-126">指定欄位具有相對的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="87b92-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87b92-127">需求</span><span class="sxs-lookup"><span data-stu-id="87b92-127">Requirements</span></span>  
 <span data-ttu-id="87b92-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87b92-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87b92-129">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="87b92-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="87b92-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87b92-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b92-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87b92-131">See also</span></span>

- [<span data-ttu-id="87b92-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="87b92-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
