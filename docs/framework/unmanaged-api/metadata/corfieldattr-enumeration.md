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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e909680428c7957da2283d13f5676329d953bf22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781887"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="05897-102">CorFieldAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="05897-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="05897-103">包含值，這些值描述與欄位有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="05897-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05897-104">語法</span><span class="sxs-lookup"><span data-stu-id="05897-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="05897-105">成員</span><span class="sxs-lookup"><span data-stu-id="05897-105">Members</span></span>  
  
|<span data-ttu-id="05897-106">成員</span><span class="sxs-lookup"><span data-stu-id="05897-106">Member</span></span>|<span data-ttu-id="05897-107">描述</span><span class="sxs-lookup"><span data-stu-id="05897-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="05897-108">指定的協助工具資訊。</span><span class="sxs-lookup"><span data-stu-id="05897-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="05897-109">指定無法參考的欄位。</span><span class="sxs-lookup"><span data-stu-id="05897-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="05897-110">指定欄位只能由其父型別存取。</span><span class="sxs-lookup"><span data-stu-id="05897-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="05897-111">指定的欄位是由其組件中的衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="05897-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="05897-112">指定欄位可存取其組件中的所有型別。</span><span class="sxs-lookup"><span data-stu-id="05897-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="05897-113">指定欄位只能由其類型存取，而且衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="05897-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="05897-114">指定的欄位是可由衍生的類別和其組件中的所有型別存取。</span><span class="sxs-lookup"><span data-stu-id="05897-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="05897-115">指定欄位可存取此範圍的可見性與所有類型。</span><span class="sxs-lookup"><span data-stu-id="05897-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="05897-116">指定的欄位是其類型的成員，而不是執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="05897-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="05897-117">指定在初始化之後，無法變更的欄位。</span><span class="sxs-lookup"><span data-stu-id="05897-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="05897-118">指定欄位值為編譯時間常數。</span><span class="sxs-lookup"><span data-stu-id="05897-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="05897-119">指定當其類型為遠端時，則不會序列化的欄位。</span><span class="sxs-lookup"><span data-stu-id="05897-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="05897-120">指定欄位是特殊的且其名稱描述方式。</span><span class="sxs-lookup"><span data-stu-id="05897-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="05897-121">指定欄位的實作會經由 PInvoke 被轉送。</span><span class="sxs-lookup"><span data-stu-id="05897-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="05897-122">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="05897-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="05897-123">指定 common language runtime 中繼資料內部 Api 應該檢查名稱編碼方式。</span><span class="sxs-lookup"><span data-stu-id="05897-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="05897-124">指定欄位含有封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="05897-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="05897-125">指定欄位含有預設值。</span><span class="sxs-lookup"><span data-stu-id="05897-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="05897-126">指定欄位含有相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="05897-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05897-127">需求</span><span class="sxs-lookup"><span data-stu-id="05897-127">Requirements</span></span>  
 <span data-ttu-id="05897-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05897-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05897-129">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="05897-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="05897-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05897-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05897-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05897-131">See also</span></span>

- [<span data-ttu-id="05897-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="05897-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
