---
title: IMetaDataImport2::GetGenericParamConstraintProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 8beaea0b7493b7cea76466bb15355cfc5c6d5c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702700"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="7ea19-102">IMetaDataImport2::GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="7ea19-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>

<span data-ttu-id="7ea19-103">取得與指定之條件約束 token 所表示之泛型參數條件約束相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7ea19-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ea19-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ea19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ea19-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ea19-105">Parameters</span></span>  

 `gpc`  
 <span data-ttu-id="7ea19-106">在要傳回中繼資料之泛型參數條件約束的標記。</span><span class="sxs-lookup"><span data-stu-id="7ea19-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="7ea19-107">擴展Token 的指標，代表受條件約束的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="7ea19-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="7ea19-108">擴展TypeDef、TypeRef 或 TypeSpec token 的指標，表示上的條件約束 `ptGenericParam` 。</span><span class="sxs-lookup"><span data-stu-id="7ea19-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ea19-109">需求</span><span class="sxs-lookup"><span data-stu-id="7ea19-109">Requirements</span></span>  

 <span data-ttu-id="7ea19-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ea19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ea19-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7ea19-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ea19-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7ea19-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ea19-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ea19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea19-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ea19-114">See also</span></span>

- [<span data-ttu-id="7ea19-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7ea19-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="7ea19-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7ea19-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
