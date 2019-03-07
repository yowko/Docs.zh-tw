---
title: IMetaDataImport::FindTypeDefByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d2d7f9b459e5a46793d44728a9fea269ca47887
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492383"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="5478e-102">IMetaDataImport::FindTypeDefByName 方法</span><span class="sxs-lookup"><span data-stu-id="5478e-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="5478e-103">取得指標的 TypeDef 中繼資料語彙基元<xref:System.Type>具有指定名稱。</span><span class="sxs-lookup"><span data-stu-id="5478e-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5478e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5478e-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5478e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5478e-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5478e-106">[in]要取得的 TypeDef 語彙基元的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5478e-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="5478e-107">[in]TypeDef 或 TypeRef 語彙基元代表封入類別。</span><span class="sxs-lookup"><span data-stu-id="5478e-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="5478e-108">如果要尋找的類型不是巢狀的類別，請將此值設為 NULL。</span><span class="sxs-lookup"><span data-stu-id="5478e-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5478e-109">[out]相符的 TypeDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="5478e-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5478e-110">需求</span><span class="sxs-lookup"><span data-stu-id="5478e-110">Requirements</span></span>  
 <span data-ttu-id="5478e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5478e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5478e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5478e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5478e-113">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5478e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5478e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5478e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5478e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5478e-115">See also</span></span>
- [<span data-ttu-id="5478e-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5478e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5478e-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5478e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
