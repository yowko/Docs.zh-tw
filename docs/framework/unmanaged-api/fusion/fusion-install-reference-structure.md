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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec18d5d5a6574cb0e08a6c4d6eaedcbcbf6886cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759356"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="c3ef5-102">FUSION_INSTALL_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="c3ef5-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="c3ef5-103">表示應用程式對應用程式已安裝在全域組件快取中的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ef5-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3ef5-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="c3ef5-105">成員</span><span class="sxs-lookup"><span data-stu-id="c3ef5-105">Members</span></span>  
  
|<span data-ttu-id="c3ef5-106">成員</span><span class="sxs-lookup"><span data-stu-id="c3ef5-106">Member</span></span>|<span data-ttu-id="c3ef5-107">描述</span><span class="sxs-lookup"><span data-stu-id="c3ef5-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="c3ef5-108">結構，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="c3ef5-109">保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-109">Reserved for future extensibility.</span></span> <span data-ttu-id="c3ef5-110">此值必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="c3ef5-111">加入參考的實體。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-111">The entity that adds the reference.</span></span> <span data-ttu-id="c3ef5-112">這個欄位可以有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c3ef5-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="c3ef5-113">-FUSION_REFCOUNT_MSI_GUID:使用 Microsoft Windows Installer 所安裝的應用程式所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="c3ef5-114">`szIdentifier`欄位設定為`MSI`，而`szNonCanonicalData` 欄位設為`Windows Installer`。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="c3ef5-115">此配置會使用 Windows 並排顯示組件。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="c3ef5-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID:會出現在應用程式所參考的組件**新增/移除程式**介面。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="c3ef5-117">`szIdentifier`欄位提供與將應用程式註冊權杖**新增/移除程式**介面。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="c3ef5-118">-FUSION_REFCOUNT_FILEPATH_GUID:組件參考的應用程式，由檔案系統中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="c3ef5-119">`szIdentifier`欄位會提供這個檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="c3ef5-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID:應用程式只能由不透明的字串表示所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="c3ef5-121">`szIdentifier`欄位提供不透明的字串。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="c3ef5-122">當您移除此值時，全域組件快取不會檢查存在的不透明的參考。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="c3ef5-123">-FUSION_REFCOUNT_OSINSTALL_GUID:這個值已保留。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="c3ef5-124">唯一的字串，可識別在全域組件快取中安裝組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="c3ef5-125">其值的值取決於`guidScheme`欄位。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="c3ef5-126">只要加入參考的實體會辨識字串。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="c3ef5-127">全域組件快取會儲存這個字串中，但不會使用它。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3ef5-128">需求</span><span class="sxs-lookup"><span data-stu-id="c3ef5-128">Requirements</span></span>  
 <span data-ttu-id="c3ef5-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3ef5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ef5-130">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c3ef5-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c3ef5-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ef5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ef5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ef5-132">See also</span></span>

- [<span data-ttu-id="c3ef5-133">融合結構</span><span class="sxs-lookup"><span data-stu-id="c3ef5-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="c3ef5-134">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="c3ef5-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
