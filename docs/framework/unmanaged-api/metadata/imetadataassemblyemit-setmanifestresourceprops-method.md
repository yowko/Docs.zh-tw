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
ms.openlocfilehash: c46a3bc34ba7efa760e50416e9a6c39779727813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708916"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="03ff7-102">IMetaDataAssemblyEmit::SetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="03ff7-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="03ff7-103">修改指定的 `ManifestResource` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="03ff7-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ff7-104">語法</span><span class="sxs-lookup"><span data-stu-id="03ff7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03ff7-105">參數</span><span class="sxs-lookup"><span data-stu-id="03ff7-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="03ff7-106">在指定 `ManifestResource` 要修改之元資料結構的標記。</span><span class="sxs-lookup"><span data-stu-id="03ff7-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="03ff7-107">在 `File` `AssemblyRef` 對應至資源提供者之類型的標記。</span><span class="sxs-lookup"><span data-stu-id="03ff7-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="03ff7-108">在檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="03ff7-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="03ff7-109">在旗標值的位元組合，這些值會指定資源的屬性。</span><span class="sxs-lookup"><span data-stu-id="03ff7-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ff7-110">備註</span><span class="sxs-lookup"><span data-stu-id="03ff7-110">Remarks</span></span>  

 <span data-ttu-id="03ff7-111">若要建立 `ManifestResource` 元資料結構，請使用 [IMetaDataAssemblyEmit：:D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="03ff7-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ff7-112">需求</span><span class="sxs-lookup"><span data-stu-id="03ff7-112">Requirements</span></span>  

 <span data-ttu-id="03ff7-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03ff7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ff7-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="03ff7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03ff7-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="03ff7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03ff7-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ff7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ff7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ff7-117">See also</span></span>

- [<span data-ttu-id="03ff7-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="03ff7-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
