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
ms.openlocfilehash: 74088d1cd018bb07406fc7d00ff83d783a98b663
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450236"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="3aad2-102">CorMethodAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="3aad2-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="3aad2-103">包含描述方法功能的值。</span><span class="sxs-lookup"><span data-stu-id="3aad2-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aad2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3aad2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3aad2-105">Members</span><span class="sxs-lookup"><span data-stu-id="3aad2-105">Members</span></span>  
  
|<span data-ttu-id="3aad2-106">成員</span><span class="sxs-lookup"><span data-stu-id="3aad2-106">Member</span></span>|<span data-ttu-id="3aad2-107">描述</span><span class="sxs-lookup"><span data-stu-id="3aad2-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="3aad2-108">指定成員存取權。</span><span class="sxs-lookup"><span data-stu-id="3aad2-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="3aad2-109">指定無法參考成員。</span><span class="sxs-lookup"><span data-stu-id="3aad2-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="3aad2-110">指定成員只能由父類型存取。</span><span class="sxs-lookup"><span data-stu-id="3aad2-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="3aad2-111">指定成員只能由這個元件中的子類型存取。</span><span class="sxs-lookup"><span data-stu-id="3aad2-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="3aad2-112">指定成員由元件中的任何人存取然後順著。</span><span class="sxs-lookup"><span data-stu-id="3aad2-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="3aad2-113">指定成員只能由類型和子類型存取。</span><span class="sxs-lookup"><span data-stu-id="3aad2-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="3aad2-114">指定成員可由衍生類別和其元件中的其他類型存取。</span><span class="sxs-lookup"><span data-stu-id="3aad2-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="3aad2-115">指定成員可由具有範圍存取權的所有類型存取。</span><span class="sxs-lookup"><span data-stu-id="3aad2-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="3aad2-116">指定將成員定義為類型的一部分，而不是實例的成員。</span><span class="sxs-lookup"><span data-stu-id="3aad2-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="3aad2-117">指定無法覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="3aad2-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="3aad2-118">指定可覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="3aad2-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="3aad2-119">指定方法會依名稱和簽章隱藏，而不只是依名稱。</span><span class="sxs-lookup"><span data-stu-id="3aad2-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="3aad2-120">指定虛擬資料表版面配置。</span><span class="sxs-lookup"><span data-stu-id="3aad2-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="3aad2-121">指定要在虛擬資料表中重複使用用於這個方法的位置。</span><span class="sxs-lookup"><span data-stu-id="3aad2-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="3aad2-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="3aad2-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="3aad2-123">指定方法一律取得虛擬資料表中的新位置。</span><span class="sxs-lookup"><span data-stu-id="3aad2-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="3aad2-124">指定方法可以被可見的相同類型覆寫。</span><span class="sxs-lookup"><span data-stu-id="3aad2-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="3aad2-125">指定不執行方法。</span><span class="sxs-lookup"><span data-stu-id="3aad2-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="3aad2-126">指定方法是特殊的，而且其名稱會描述如何。</span><span class="sxs-lookup"><span data-stu-id="3aad2-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="3aad2-127">指定使用 PInvoke 轉送方法執行。</span><span class="sxs-lookup"><span data-stu-id="3aad2-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="3aad2-128">指定方法是匯出至非受控程式碼的 managed 方法。</span><span class="sxs-lookup"><span data-stu-id="3aad2-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="3aad2-129">保留供 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="3aad2-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="3aad2-130">指定通用語言執行時間應該檢查方法名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="3aad2-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="3aad2-131">指定方法具有相關聯的安全性。</span><span class="sxs-lookup"><span data-stu-id="3aad2-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="3aad2-132">指定方法呼叫另一個包含安全性程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="3aad2-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aad2-133">需求</span><span class="sxs-lookup"><span data-stu-id="3aad2-133">Requirements</span></span>  
 <span data-ttu-id="3aad2-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3aad2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aad2-135">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="3aad2-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3aad2-136">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aad2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aad2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3aad2-137">See also</span></span>

- [<span data-ttu-id="3aad2-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="3aad2-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
