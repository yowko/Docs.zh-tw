---
title: IMetaDataAssemblyEmit::SetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177857"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="40f87-102">IMetaDataAssemblyEmit::SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="40f87-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="40f87-103">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="40f87-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f87-104">語法</span><span class="sxs-lookup"><span data-stu-id="40f87-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f87-105">參數</span><span class="sxs-lookup"><span data-stu-id="40f87-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="40f87-106">[在]指定要修改的`ExportedType`元資料結構的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="40f87-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="40f87-107">[在]指定如何實現此類型的`File`權杖`AssemblyRef`的類型`ExportedType`。</span><span class="sxs-lookup"><span data-stu-id="40f87-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="40f87-108">[在]代碼`TypeDef`檔中引用的權杖。</span><span class="sxs-lookup"><span data-stu-id="40f87-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="40f87-109">[在]指定類型屬性的值的位組合。</span><span class="sxs-lookup"><span data-stu-id="40f87-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f87-110">備註</span><span class="sxs-lookup"><span data-stu-id="40f87-110">Remarks</span></span>  
 <span data-ttu-id="40f87-111">要創建`ExportedType`元資料結構，請使用[IMetaDataAssemblyEmit：:Defineexportetype 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="40f87-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f87-112">需求</span><span class="sxs-lookup"><span data-stu-id="40f87-112">Requirements</span></span>  
 <span data-ttu-id="40f87-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40f87-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f87-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="40f87-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40f87-115">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="40f87-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40f87-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f87-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f87-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40f87-117">See also</span></span>

- [<span data-ttu-id="40f87-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="40f87-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
