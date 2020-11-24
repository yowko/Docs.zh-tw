---
title: FUSION_INSTALL_REFERENCE 結構
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688805"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="7621a-102">FUSION_INSTALL_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="7621a-102">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="7621a-103">表示應用程式對應用程式已安裝在全域組件快取中之元件的參考。</span><span class="sxs-lookup"><span data-stu-id="7621a-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7621a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7621a-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="7621a-105">成員</span><span class="sxs-lookup"><span data-stu-id="7621a-105">Members</span></span>  
  
|<span data-ttu-id="7621a-106">member</span><span class="sxs-lookup"><span data-stu-id="7621a-106">Member</span></span>|<span data-ttu-id="7621a-107">描述</span><span class="sxs-lookup"><span data-stu-id="7621a-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="7621a-108">結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7621a-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="7621a-109">保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="7621a-109">Reserved for future extensibility.</span></span> <span data-ttu-id="7621a-110">這個值必須是 0 (零) 。</span><span class="sxs-lookup"><span data-stu-id="7621a-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="7621a-111">加入參考的實體。</span><span class="sxs-lookup"><span data-stu-id="7621a-111">The entity that adds the reference.</span></span> <span data-ttu-id="7621a-112">這個欄位可以具有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="7621a-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="7621a-113">-FUSION_REFCOUNT_MSI_GUID：使用 Microsoft Windows Installer 所安裝的應用程式所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="7621a-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="7621a-114">`szIdentifier`欄位設定為 `MSI` ，而且 `szNonCanonicalData` 欄位設定為 `Windows Installer` 。</span><span class="sxs-lookup"><span data-stu-id="7621a-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="7621a-115">此配置用於 Windows 並存元件。</span><span class="sxs-lookup"><span data-stu-id="7621a-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="7621a-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID：應用程式會參考出現在 [ **新增/移除程式** ] 介面中的元件。</span><span class="sxs-lookup"><span data-stu-id="7621a-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="7621a-117">`szIdentifier`欄位提供使用 [**新增/移除程式**] 介面註冊應用程式的權杖。</span><span class="sxs-lookup"><span data-stu-id="7621a-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="7621a-118">-FUSION_REFCOUNT_FILEPATH_GUID：元件是由檔案系統中的檔案所代表的應用程式所參考。</span><span class="sxs-lookup"><span data-stu-id="7621a-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="7621a-119">`szIdentifier`欄位提供此檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7621a-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="7621a-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID：元件是由只由不透明字串所表示的應用程式所參考。</span><span class="sxs-lookup"><span data-stu-id="7621a-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="7621a-121">`szIdentifier`欄位提供此不透明字串。</span><span class="sxs-lookup"><span data-stu-id="7621a-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="7621a-122">當您移除這個值時，全域組件快取不會檢查是否存在不透明的參考。</span><span class="sxs-lookup"><span data-stu-id="7621a-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="7621a-123">-FUSION_REFCOUNT_OSINSTALL_GUID：此值為 reserved。</span><span class="sxs-lookup"><span data-stu-id="7621a-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="7621a-124">唯一的字串，可識別在全域組件快取中安裝元件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7621a-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="7621a-125">它的值會根據欄位的值而定 `guidScheme` 。</span><span class="sxs-lookup"><span data-stu-id="7621a-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="7621a-126">只有加入參考的實體才會瞭解的字串。</span><span class="sxs-lookup"><span data-stu-id="7621a-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="7621a-127">全域組件快取會儲存這個字串，但不會使用它。</span><span class="sxs-lookup"><span data-stu-id="7621a-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7621a-128">需求</span><span class="sxs-lookup"><span data-stu-id="7621a-128">Requirements</span></span>  

 <span data-ttu-id="7621a-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7621a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7621a-130">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="7621a-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7621a-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7621a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7621a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7621a-132">See also</span></span>

- [<span data-ttu-id="7621a-133">融合結構</span><span class="sxs-lookup"><span data-stu-id="7621a-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="7621a-134">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="7621a-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
