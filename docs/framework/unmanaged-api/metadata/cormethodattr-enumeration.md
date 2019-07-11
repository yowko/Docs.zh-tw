---
title: CorMethodAttr 列舉
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff298f73f02f148fc389f389ba86fd9a550998c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781779"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="483d3-102">CorMethodAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="483d3-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="483d3-103">包含描述方法的功能值。</span><span class="sxs-lookup"><span data-stu-id="483d3-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="483d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="483d3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="483d3-105">成員</span><span class="sxs-lookup"><span data-stu-id="483d3-105">Members</span></span>  
  
|<span data-ttu-id="483d3-106">成員</span><span class="sxs-lookup"><span data-stu-id="483d3-106">Member</span></span>|<span data-ttu-id="483d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="483d3-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="483d3-108">指定成員存取。</span><span class="sxs-lookup"><span data-stu-id="483d3-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="483d3-109">指定成員不能參考。</span><span class="sxs-lookup"><span data-stu-id="483d3-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="483d3-110">指定成員只能由父型別存取。</span><span class="sxs-lookup"><span data-stu-id="483d3-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="483d3-111">指定成員可存取由子型別只能在這個組件中。</span><span class="sxs-lookup"><span data-stu-id="483d3-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="483d3-112">指定組件中的任何人都可以存取此成員。</span><span class="sxs-lookup"><span data-stu-id="483d3-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="483d3-113">指定成員只能由型別和子型別存取。</span><span class="sxs-lookup"><span data-stu-id="483d3-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="483d3-114">指定成員可存取由衍生的類別和其組件中的其他型別。</span><span class="sxs-lookup"><span data-stu-id="483d3-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="483d3-115">指定成員為可存取的所有型別存取範圍。</span><span class="sxs-lookup"><span data-stu-id="483d3-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="483d3-116">指定此成員定義為類型的一部分，而不是執行個體的成員。</span><span class="sxs-lookup"><span data-stu-id="483d3-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="483d3-117">指定無法覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="483d3-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="483d3-118">指定可以覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="483d3-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="483d3-119">指定的方法會在依名稱和簽章，而不是只依名稱隱藏。</span><span class="sxs-lookup"><span data-stu-id="483d3-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="483d3-120">指定虛擬資料表配置。</span><span class="sxs-lookup"><span data-stu-id="483d3-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="483d3-121">指定用於虛擬資料表中，這個方法的位置可重複使用。</span><span class="sxs-lookup"><span data-stu-id="483d3-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="483d3-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="483d3-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="483d3-123">指定此方法一律會取得虛擬資料表中的新位置。</span><span class="sxs-lookup"><span data-stu-id="483d3-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="483d3-124">指定可以在相同的型別，它會顯示所覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="483d3-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="483d3-125">指定的方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="483d3-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="483d3-126">指定的方法是特殊的且其名稱描述方式。</span><span class="sxs-lookup"><span data-stu-id="483d3-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="483d3-127">指定方法實作會轉送使用 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="483d3-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="483d3-128">指定的方法是匯出至 unmanaged 程式碼的 managed 的方法。</span><span class="sxs-lookup"><span data-stu-id="483d3-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="483d3-129">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="483d3-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="483d3-130">指定 common language runtime 應該檢查方法名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="483d3-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="483d3-131">指定的方法具有與它相關聯的安全性。</span><span class="sxs-lookup"><span data-stu-id="483d3-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="483d3-132">指定此方法會呼叫含有安全程式碼的另一種方法。</span><span class="sxs-lookup"><span data-stu-id="483d3-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="483d3-133">需求</span><span class="sxs-lookup"><span data-stu-id="483d3-133">Requirements</span></span>  
 <span data-ttu-id="483d3-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="483d3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="483d3-135">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="483d3-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="483d3-136">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="483d3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483d3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="483d3-137">See also</span></span>

- [<span data-ttu-id="483d3-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="483d3-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
