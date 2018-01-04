---
title: "IMetaDataAssemblyEmit::SetExportedTypeProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bebcf827488912431cb0f94f5527d3445fc41125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="73b08-102">IMetaDataAssemblyEmit::SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="73b08-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="73b08-103">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="73b08-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b08-104">語法</span><span class="sxs-lookup"><span data-stu-id="73b08-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73b08-105">參數</span><span class="sxs-lookup"><span data-stu-id="73b08-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="73b08-106">[in]指定的中繼資料語彙基元`ExportedType`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="73b08-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="73b08-107">[in]類型的語彙基元`File`， `AssemblyRef`，或`ExportedType`，指定此類型的實作方式。</span><span class="sxs-lookup"><span data-stu-id="73b08-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="73b08-108">[in]`TypeDef`程式碼檔案中參考的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="73b08-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="73b08-109">[in]指定類型的屬性值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="73b08-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73b08-110">備註</span><span class="sxs-lookup"><span data-stu-id="73b08-110">Remarks</span></span>  
 <span data-ttu-id="73b08-111">若要建立`ExportedType`中繼資料結構，使用[imetadataassemblyemit:: Defineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="73b08-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73b08-112">需求</span><span class="sxs-lookup"><span data-stu-id="73b08-112">Requirements</span></span>  
 <span data-ttu-id="73b08-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73b08-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b08-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73b08-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73b08-115">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="73b08-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73b08-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b08-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b08-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="73b08-117">See Also</span></span>  
 [<span data-ttu-id="73b08-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="73b08-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
