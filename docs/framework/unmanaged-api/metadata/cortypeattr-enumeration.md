---
title: "CorTypeAttr 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTypeAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTypeAttr
helpviewer_keywords: CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 501488c0ac03ebf508145572ed73163d7940bfbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="3b7d2-102">CorTypeAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="3b7d2-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="3b7d2-103">包含值，這些值表示類型中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b7d2-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="3b7d2-105">成員</span><span class="sxs-lookup"><span data-stu-id="3b7d2-105">Members</span></span>  
  
|<span data-ttu-id="3b7d2-106">成員</span><span class="sxs-lookup"><span data-stu-id="3b7d2-106">Member</span></span>|<span data-ttu-id="3b7d2-107">描述</span><span class="sxs-lookup"><span data-stu-id="3b7d2-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="3b7d2-108">用於型別可視性資訊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="3b7d2-109">指定的類型不是公用的範圍中。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="3b7d2-110">指定的類型是公用的範圍中。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="3b7d2-111">指定的類型使用巢狀公用可視性。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="3b7d2-112">指定的類型巢狀具有私用的可視性。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="3b7d2-113">指定的型別使用家族可視性所產生的巢狀。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="3b7d2-114">指定的類型巢狀與組件可見性。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="3b7d2-115">指定型別使用家族和組件可視性所產生的巢狀。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="3b7d2-116">指定型別使用家族或組件可視性所產生的巢狀。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="3b7d2-117">取得類型的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="3b7d2-118">指定此類型的欄位會自動配置。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="3b7d2-119">指定此類型的欄位會循序配置。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="3b7d2-120">指定明確提供該欄位的配置。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="3b7d2-121">取得類型的語意資訊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="3b7d2-122">指定此類型為類別。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="3b7d2-123">指定此類型為介面。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="3b7d2-124">指定此類型為抽象。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="3b7d2-125">指定類型，無法擴充。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="3b7d2-126">指定類別名稱是特殊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-126">Specifies that the class name is special.</span></span> <span data-ttu-id="3b7d2-127">其名稱會說明如何。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="3b7d2-128">指定的類型匯入。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="3b7d2-129">指定的型別是可序列化。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="3b7d2-130">指定此類型為[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="3b7d2-131">取得如何編碼和格式字串的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="3b7d2-132">指定此類型會解譯為 ANSI LPTSTR。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="3b7d2-133">指定此類型會解譯為 Unicode LPTSTR。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="3b7d2-134">指定此類型會自動解譯 LPTSTR。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="3b7d2-135">指定類型具有非標準的編碼，依指定`CustomFormatMask`。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="3b7d2-136">您可以使用這個遮罩，取得原生 interop 的非標準編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="3b7d2-137">未指定這些兩位元值的意義。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="3b7d2-138">指定第一次嘗試存取的靜態欄位之前，必須初始化型別。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="3b7d2-139">指定的已匯出類型，以及類型轉送子。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="3b7d2-140">這個旗標，而且下列旗標，則會由 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="3b7d2-141">指定通用語言執行平台應該檢查名稱編碼。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="3b7d2-142">指定類型具有與其相關聯的安全性。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b7d2-143">需求</span><span class="sxs-lookup"><span data-stu-id="3b7d2-143">Requirements</span></span>  
 <span data-ttu-id="3b7d2-144">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b7d2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7d2-145">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3b7d2-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3b7d2-146">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7d2-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d2-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b7d2-147">See Also</span></span>  
 [<span data-ttu-id="3b7d2-148">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="3b7d2-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
