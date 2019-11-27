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
ms.openlocfilehash: 0adf4f91e1bc7bfb72f634cb3bf038710198b74f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437133"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="11990-102">IMetaDataImport::GetNestedClassProps 方法</span><span class="sxs-lookup"><span data-stu-id="11990-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="11990-103">取得指定之嵌套型別之父 <xref:System.Type> 的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="11990-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11990-104">語法</span><span class="sxs-lookup"><span data-stu-id="11990-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11990-105">參數</span><span class="sxs-lookup"><span data-stu-id="11990-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="11990-106">在TypeDef token，代表要傳回之父類別 token 的 <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="11990-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="11990-107">脫銷`tdNestedClass` 的 <xref:System.Type> 之 TypeDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="11990-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11990-108">需求</span><span class="sxs-lookup"><span data-stu-id="11990-108">Requirements</span></span>  
 <span data-ttu-id="11990-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11990-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11990-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="11990-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11990-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11990-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11990-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11990-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11990-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11990-113">See also</span></span>

- [<span data-ttu-id="11990-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="11990-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="11990-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="11990-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
