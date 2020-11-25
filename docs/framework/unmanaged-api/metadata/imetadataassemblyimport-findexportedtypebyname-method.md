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
ms.openlocfilehash: b1672d98d76241e5af4b6b60a38785f1278e15a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731588"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="5ce3a-102">IMetaDataAssemblyImport::FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="5ce3a-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="5ce3a-103">取得匯出類型的指標，並指定其名稱和封入類型。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ce3a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ce3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ce3a-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="5ce3a-106">在匯出之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="5ce3a-107">在匯出類型之封入類別的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="5ce3a-108">`mdExportedTypeNil`如果要求的匯出型別不是嵌套型別，則此值為。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="5ce3a-109">擴展Token 的指標 `mdExportedType` ，表示匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce3a-110">備註</span><span class="sxs-lookup"><span data-stu-id="5ce3a-110">Remarks</span></span>  

 <span data-ttu-id="5ce3a-111">`FindExportedTypeByName`方法會使用 common language runtime 所採用的標準規則來解析參考。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce3a-112">需求</span><span class="sxs-lookup"><span data-stu-id="5ce3a-112">Requirements</span></span>  

 <span data-ttu-id="5ce3a-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ce3a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce3a-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5ce3a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ce3a-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5ce3a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ce3a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce3a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ce3a-117">See also</span></span>

- [<span data-ttu-id="5ce3a-118">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="5ce3a-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="5ce3a-119">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="5ce3a-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
