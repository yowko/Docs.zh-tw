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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a7b7b498cc4e52b8be3f43ae52293de380d9f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182256"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="e0461-102">IMetaDataAssemblyImport::FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="e0461-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="e0461-103">取得指標至匯出的型別，指定其名稱與封入型別。</span><span class="sxs-lookup"><span data-stu-id="e0461-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0461-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0461-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0461-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0461-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e0461-106">[in]匯出的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e0461-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="e0461-107">[in]匯出類型的封入類別之中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0461-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="e0461-108">這個值是`mdExportedTypeNil`如果要求的匯出型別不是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="e0461-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="e0461-109">[out]指標`mdExportedType`表示匯出的型別語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0461-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0461-110">備註</span><span class="sxs-lookup"><span data-stu-id="e0461-110">Remarks</span></span>  
 <span data-ttu-id="e0461-111">`FindExportedTypeByName`方法會使用解析參考的 common language runtime 所採用的標準規則。</span><span class="sxs-lookup"><span data-stu-id="e0461-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0461-112">需求</span><span class="sxs-lookup"><span data-stu-id="e0461-112">Requirements</span></span>  
 <span data-ttu-id="e0461-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0461-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0461-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0461-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0461-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e0461-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e0461-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e0461-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0461-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0461-117">See also</span></span>

- [<span data-ttu-id="e0461-118">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="e0461-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e0461-119">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="e0461-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
