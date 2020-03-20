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
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175989"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="57cf4-102">IMetaDataAssemblyImport::FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="57cf4-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="57cf4-103">獲取指向匯出類型的指標，給定其名稱和封閉類型。</span><span class="sxs-lookup"><span data-stu-id="57cf4-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cf4-104">語法</span><span class="sxs-lookup"><span data-stu-id="57cf4-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57cf4-105">參數</span><span class="sxs-lookup"><span data-stu-id="57cf4-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="57cf4-106">[在]匯出類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="57cf4-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="57cf4-107">[在]匯出類型的封閉類的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="57cf4-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="57cf4-108">此值是`mdExportedTypeNil`請求的匯出類型不是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="57cf4-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="57cf4-109">[出]指向表示匯出類型的`mdExportedType`權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="57cf4-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57cf4-110">備註</span><span class="sxs-lookup"><span data-stu-id="57cf4-110">Remarks</span></span>  
 <span data-ttu-id="57cf4-111">該方法`FindExportedTypeByName`使用通用語言運行時採用的標準規則來解決引用。</span><span class="sxs-lookup"><span data-stu-id="57cf4-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57cf4-112">需求</span><span class="sxs-lookup"><span data-stu-id="57cf4-112">Requirements</span></span>  
 <span data-ttu-id="57cf4-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57cf4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57cf4-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="57cf4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57cf4-115">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="57cf4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57cf4-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57cf4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cf4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57cf4-117">See also</span></span>

- [<span data-ttu-id="57cf4-118">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="57cf4-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="57cf4-119">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="57cf4-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
