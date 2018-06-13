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
ms.openlocfilehash: 4685d1a23fdf1874817522a16ccd428d81acd1ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433226"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="cf834-102">FUSION_INSTALL_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="cf834-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="cf834-103">表示應用程式建立應用程式已安裝在全域組件快取中的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="cf834-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf834-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf834-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="cf834-105">成員</span><span class="sxs-lookup"><span data-stu-id="cf834-105">Members</span></span>  
  
|<span data-ttu-id="cf834-106">成員</span><span class="sxs-lookup"><span data-stu-id="cf834-106">Member</span></span>|<span data-ttu-id="cf834-107">描述</span><span class="sxs-lookup"><span data-stu-id="cf834-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="cf834-108">結構，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="cf834-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="cf834-109">保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="cf834-109">Reserved for future extensibility.</span></span> <span data-ttu-id="cf834-110">此值必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="cf834-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="cf834-111">加入參考的實體。</span><span class="sxs-lookup"><span data-stu-id="cf834-111">The entity that adds the reference.</span></span> <span data-ttu-id="cf834-112">這個欄位可以有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cf834-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="cf834-113">-FUSION_REFCOUNT_MSI_GUID： 使用 Microsoft Windows Installer 已安裝的應用程式所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="cf834-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="cf834-114">`szIdentifier`欄位設定為`MSI`，而`szNonCanonicalData`欄位設定為`Windows Installer`。</span><span class="sxs-lookup"><span data-stu-id="cf834-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="cf834-115">這種配置適用於 Windows 的並存組件。</span><span class="sxs-lookup"><span data-stu-id="cf834-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="cf834-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID： 會出現在應用程式參考的組件**新增/移除程式**介面。</span><span class="sxs-lookup"><span data-stu-id="cf834-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="cf834-117">`szIdentifier`欄位提供的語彙基元註冊此應用程式與**新增/移除程式**介面。</span><span class="sxs-lookup"><span data-stu-id="cf834-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="cf834-118">-FUSION_REFCOUNT_FILEPATH_GUID： 應用程式由檔案系統中的檔案所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="cf834-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="cf834-119">`szIdentifier`欄位會提供這個檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="cf834-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="cf834-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID： 應用程式只能由不透明的字串表示所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="cf834-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="cf834-121">`szIdentifier`欄位提供的不透明的字串。</span><span class="sxs-lookup"><span data-stu-id="cf834-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="cf834-122">全域組件快取不會檢查不透明參考存在，當您移除此值。</span><span class="sxs-lookup"><span data-stu-id="cf834-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="cf834-123">-FUSION_REFCOUNT_OSINSTALL_GUID： 保留此值。</span><span class="sxs-lookup"><span data-stu-id="cf834-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="cf834-124">識別在全域組件快取中安裝組件的應用程式的唯一字串。</span><span class="sxs-lookup"><span data-stu-id="cf834-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="cf834-125">它的值而定的值`guidScheme`欄位。</span><span class="sxs-lookup"><span data-stu-id="cf834-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="cf834-126">字串，只會將參考加入的實體了解。</span><span class="sxs-lookup"><span data-stu-id="cf834-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="cf834-127">全域組件快取會儲存這個字串，但不是會使用它。</span><span class="sxs-lookup"><span data-stu-id="cf834-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf834-128">需求</span><span class="sxs-lookup"><span data-stu-id="cf834-128">Requirements</span></span>  
 <span data-ttu-id="cf834-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf834-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf834-130">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cf834-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cf834-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf834-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf834-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf834-132">See Also</span></span>  
 [<span data-ttu-id="cf834-133">融合結構</span><span class="sxs-lookup"><span data-stu-id="cf834-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="cf834-134">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="cf834-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
