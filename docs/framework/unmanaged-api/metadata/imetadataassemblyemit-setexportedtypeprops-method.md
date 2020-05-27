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
ms.openlocfilehash: fa4f1f57cb8fe1ca81bbad6438a88bb43c48e7bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008075"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="40276-102">IMetaDataAssemblyEmit::SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="40276-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="40276-103">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="40276-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40276-104">語法</span><span class="sxs-lookup"><span data-stu-id="40276-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40276-105">參數</span><span class="sxs-lookup"><span data-stu-id="40276-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="40276-106">在元資料標記，指定 `ExportedType` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="40276-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="40276-107">在類型 `File` 為、或的 token， `AssemblyRef` `ExportedType` 指定如何實作為此型別。</span><span class="sxs-lookup"><span data-stu-id="40276-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="40276-108">在程式 `TypeDef` 代碼檔案中參考的 token。</span><span class="sxs-lookup"><span data-stu-id="40276-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="40276-109">在值的位元組合，這個組合會指定類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="40276-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40276-110">備註</span><span class="sxs-lookup"><span data-stu-id="40276-110">Remarks</span></span>  
 <span data-ttu-id="40276-111">若要建立 `ExportedType` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="40276-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40276-112">需求</span><span class="sxs-lookup"><span data-stu-id="40276-112">Requirements</span></span>  
 <span data-ttu-id="40276-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40276-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40276-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="40276-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40276-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="40276-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40276-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40276-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40276-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40276-117">See also</span></span>

- [<span data-ttu-id="40276-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="40276-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
