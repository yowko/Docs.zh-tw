---
title: "IMetaDataImport::FindTypeDefByName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 036a177e807a2ab77a6afa74c7b811eeaaebfd29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="27e8b-102">IMetaDataImport::FindTypeDefByName 方法</span><span class="sxs-lookup"><span data-stu-id="27e8b-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="27e8b-103">取得指標的 TypeDef 中繼資料語彙基元的<xref:System.Type>具有指定名稱。</span><span class="sxs-lookup"><span data-stu-id="27e8b-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="27e8b-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27e8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="27e8b-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="27e8b-106">[in]要取得的 TypeDef 語彙基元類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="27e8b-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="27e8b-107">[in]表示封入類別的 TypeDef 或 TypeRef 權杖。</span><span class="sxs-lookup"><span data-stu-id="27e8b-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="27e8b-108">如果要尋找的類型不是巢狀的類別，設定此值為 NULL。</span><span class="sxs-lookup"><span data-stu-id="27e8b-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="27e8b-109">[out]比對的 TypeDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="27e8b-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27e8b-110">需求</span><span class="sxs-lookup"><span data-stu-id="27e8b-110">Requirements</span></span>  
 <span data-ttu-id="27e8b-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27e8b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27e8b-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27e8b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27e8b-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="27e8b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27e8b-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27e8b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e8b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="27e8b-115">See Also</span></span>  
 [<span data-ttu-id="27e8b-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="27e8b-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="27e8b-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="27e8b-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
