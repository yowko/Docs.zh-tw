---
title: IMetaDataAssemblyEmit::SetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: 74111a175b0decbc1beef7c8df5ade59d31d845b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009141"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="961f3-102">IMetaDataAssemblyEmit::SetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="961f3-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="961f3-103">修改指定的 `ManifestResource` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="961f3-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="961f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="961f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="961f3-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="961f3-106">在權杖，指定 `ManifestResource` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="961f3-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="961f3-107">在`File` `AssemblyRef` 對應至資源提供者之類型或的 token。</span><span class="sxs-lookup"><span data-stu-id="961f3-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="961f3-108">在檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="961f3-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="961f3-109">在旗標值的位元組合，指定資源的屬性。</span><span class="sxs-lookup"><span data-stu-id="961f3-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="961f3-110">備註</span><span class="sxs-lookup"><span data-stu-id="961f3-110">Remarks</span></span>  
 <span data-ttu-id="961f3-111">若要建立 `ManifestResource` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="961f3-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="961f3-112">需求</span><span class="sxs-lookup"><span data-stu-id="961f3-112">Requirements</span></span>  
 <span data-ttu-id="961f3-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="961f3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="961f3-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="961f3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="961f3-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="961f3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="961f3-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="961f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961f3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="961f3-117">See also</span></span>

- [<span data-ttu-id="961f3-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="961f3-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
