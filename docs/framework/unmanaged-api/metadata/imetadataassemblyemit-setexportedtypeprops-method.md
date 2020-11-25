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
ms.openlocfilehash: 076d027945dc27942e4b0989e14e86d829f76679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713479"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="5a93b-102">IMetaDataAssemblyEmit::SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="5a93b-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="5a93b-103">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="5a93b-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a93b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a93b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a93b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a93b-105">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="5a93b-106">在元資料標記，指定 `ExportedType` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="5a93b-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5a93b-107">在型別 `File` 為、或的 token， `AssemblyRef` `ExportedType` 可指定如何實作為此型別。</span><span class="sxs-lookup"><span data-stu-id="5a93b-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="5a93b-108">在程式 `TypeDef` 代碼檔案中參考的 token。</span><span class="sxs-lookup"><span data-stu-id="5a93b-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="5a93b-109">在值的位元組合，這些值會指定類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a93b-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a93b-110">備註</span><span class="sxs-lookup"><span data-stu-id="5a93b-110">Remarks</span></span>  

 <span data-ttu-id="5a93b-111">若要建立 `ExportedType` 元資料結構，請使用 [IMetaDataAssemblyEmit：:D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="5a93b-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a93b-112">需求</span><span class="sxs-lookup"><span data-stu-id="5a93b-112">Requirements</span></span>  

 <span data-ttu-id="5a93b-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a93b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a93b-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5a93b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a93b-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5a93b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a93b-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a93b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a93b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a93b-117">See also</span></span>

- [<span data-ttu-id="5a93b-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5a93b-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
