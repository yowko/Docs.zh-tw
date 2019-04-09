---
title: IMetaDataImport::GetNestedClassProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb5820087001a207af0c2552f91b4c17f5f78ff7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074829"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="7301b-102">IMetaDataImport::GetNestedClassProps 方法</span><span class="sxs-lookup"><span data-stu-id="7301b-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="7301b-103">取得父代語彙基元 TypeDef<xref:System.Type>指定巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="7301b-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7301b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7301b-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7301b-105">參數</span><span class="sxs-lookup"><span data-stu-id="7301b-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="7301b-106">[in]TypeDef 語彙基元，代表<xref:System.Type>傳回父類別的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7301b-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="7301b-107">[out]TypeDef 語彙基元的指標<xref:System.Type>，`tdNestedClass`巢狀方式置於。</span><span class="sxs-lookup"><span data-stu-id="7301b-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7301b-108">需求</span><span class="sxs-lookup"><span data-stu-id="7301b-108">Requirements</span></span>  
 <span data-ttu-id="7301b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7301b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7301b-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7301b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7301b-111">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7301b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7301b-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7301b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7301b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7301b-113">See also</span></span>

- [<span data-ttu-id="7301b-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7301b-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7301b-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7301b-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
