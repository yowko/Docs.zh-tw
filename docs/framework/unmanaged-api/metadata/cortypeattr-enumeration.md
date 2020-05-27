---
title: CorTypeAttr 列舉
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008959"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="1039a-102">CorTypeAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="1039a-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="1039a-103">包含值，這些值表示類型中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1039a-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1039a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1039a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="1039a-105">成員</span><span class="sxs-lookup"><span data-stu-id="1039a-105">Members</span></span>  
  
|<span data-ttu-id="1039a-106">成員</span><span class="sxs-lookup"><span data-stu-id="1039a-106">Member</span></span>|<span data-ttu-id="1039a-107">描述</span><span class="sxs-lookup"><span data-stu-id="1039a-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="1039a-108">用於類型可見度資訊。</span><span class="sxs-lookup"><span data-stu-id="1039a-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="1039a-109">指定類型不在公用範圍中。</span><span class="sxs-lookup"><span data-stu-id="1039a-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="1039a-110">指定類型在公用範圍中。</span><span class="sxs-lookup"><span data-stu-id="1039a-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="1039a-111">指定類型是以公用可見度來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="1039a-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="1039a-112">指定類型是以私用可見度來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="1039a-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="1039a-113">指定類型是以家族可見度進行內嵌。</span><span class="sxs-lookup"><span data-stu-id="1039a-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="1039a-114">指定類型是以元件可見度來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="1039a-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="1039a-115">指定類型是以系列和元件可見度來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="1039a-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="1039a-116">指定類型是以家族或元件可見度來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="1039a-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="1039a-117">取得類型的版面配置資訊。</span><span class="sxs-lookup"><span data-stu-id="1039a-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="1039a-118">指定此類型的欄位會自動設定。</span><span class="sxs-lookup"><span data-stu-id="1039a-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="1039a-119">指定以順序排列此類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="1039a-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="1039a-120">指定明確提供欄位版面配置。</span><span class="sxs-lookup"><span data-stu-id="1039a-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="1039a-121">取得類型的相關語義資訊。</span><span class="sxs-lookup"><span data-stu-id="1039a-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="1039a-122">指定此類型為類別。</span><span class="sxs-lookup"><span data-stu-id="1039a-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="1039a-123">指定此類型為介面。</span><span class="sxs-lookup"><span data-stu-id="1039a-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="1039a-124">指定此類型為抽象。</span><span class="sxs-lookup"><span data-stu-id="1039a-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="1039a-125">指定無法擴充類型。</span><span class="sxs-lookup"><span data-stu-id="1039a-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="1039a-126">指定類別名稱是特殊的。</span><span class="sxs-lookup"><span data-stu-id="1039a-126">Specifies that the class name is special.</span></span> <span data-ttu-id="1039a-127">其名稱說明如何。</span><span class="sxs-lookup"><span data-stu-id="1039a-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="1039a-128">指定要匯入的類型。</span><span class="sxs-lookup"><span data-stu-id="1039a-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="1039a-129">指定類型為可序列化。</span><span class="sxs-lookup"><span data-stu-id="1039a-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="1039a-130">指定這個類型是 Windows 執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="1039a-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="1039a-131">取得如何編碼和格式化字串的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1039a-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="1039a-132">指定此類型會將 LPTSTR 解讀為 ANSI。</span><span class="sxs-lookup"><span data-stu-id="1039a-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="1039a-133">指定此類型會將 LPTSTR 解讀為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="1039a-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="1039a-134">指定此型別會自動解讀 LPTSTR。</span><span class="sxs-lookup"><span data-stu-id="1039a-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="1039a-135">指定類型具有非標準編碼，如所指定 `CustomFormatMask` 。</span><span class="sxs-lookup"><span data-stu-id="1039a-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="1039a-136">使用此遮罩來取得原生 interop 的非標準編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="1039a-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="1039a-137">未指定這兩個位值的意義。</span><span class="sxs-lookup"><span data-stu-id="1039a-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="1039a-138">指定在第一次嘗試存取靜態欄位之前，必須先初始化型別。</span><span class="sxs-lookup"><span data-stu-id="1039a-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="1039a-139">指定匯出類型和類型轉寄站。</span><span class="sxs-lookup"><span data-stu-id="1039a-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="1039a-140">通用語言執行時間會在內部使用此旗標和下列旗標。</span><span class="sxs-lookup"><span data-stu-id="1039a-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="1039a-141">指定通用語言執行時間應該檢查名稱編碼。</span><span class="sxs-lookup"><span data-stu-id="1039a-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="1039a-142">指定類型具有相關聯的安全性。</span><span class="sxs-lookup"><span data-stu-id="1039a-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1039a-143">需求</span><span class="sxs-lookup"><span data-stu-id="1039a-143">Requirements</span></span>  
 <span data-ttu-id="1039a-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1039a-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1039a-145">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="1039a-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1039a-146">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1039a-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1039a-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1039a-147">See also</span></span>

- [<span data-ttu-id="1039a-148">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="1039a-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
