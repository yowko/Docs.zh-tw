---
title: IMetaDataAssemblyImport::FindExportedTypeByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009388"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="70f9d-102">IMetaDataAssemblyImport::FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="70f9d-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="70f9d-103">取得匯出類型的指標，並指定其名稱和封入類型。</span><span class="sxs-lookup"><span data-stu-id="70f9d-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="70f9d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70f9d-105">參數</span><span class="sxs-lookup"><span data-stu-id="70f9d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="70f9d-106">在匯出之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="70f9d-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="70f9d-107">在已匯出類型之封入類別的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="70f9d-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="70f9d-108">`mdExportedTypeNil`如果要求的匯出型別不是嵌套型別，這個值就是。</span><span class="sxs-lookup"><span data-stu-id="70f9d-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="70f9d-109">脫銷標記的指標 `mdExportedType` ，表示匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="70f9d-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f9d-110">備註</span><span class="sxs-lookup"><span data-stu-id="70f9d-110">Remarks</span></span>  
 <span data-ttu-id="70f9d-111">`FindExportedTypeByName`方法會使用 common language runtime 所採用的標準規則來解析參考。</span><span class="sxs-lookup"><span data-stu-id="70f9d-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f9d-112">需求</span><span class="sxs-lookup"><span data-stu-id="70f9d-112">Requirements</span></span>  
 <span data-ttu-id="70f9d-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70f9d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f9d-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="70f9d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70f9d-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="70f9d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70f9d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f9d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70f9d-117">See also</span></span>

- [<span data-ttu-id="70f9d-118">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="70f9d-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="70f9d-119">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="70f9d-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
