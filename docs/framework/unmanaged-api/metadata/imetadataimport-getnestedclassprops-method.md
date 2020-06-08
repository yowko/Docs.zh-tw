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
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503532"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="e1069-102">IMetaDataImport::GetNestedClassProps 方法</span><span class="sxs-lookup"><span data-stu-id="e1069-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="e1069-103">取得 <xref:System.Type> 指定之嵌套型別之父系的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="e1069-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1069-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1069-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1069-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1069-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="e1069-106">在TypeDef token，代表要傳回之 <xref:System.Type> 父類別 token 的。</span><span class="sxs-lookup"><span data-stu-id="e1069-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="e1069-107">脫銷所連結之的 TypeDef token 的指標 <xref:System.Type> `tdNestedClass` 。</span><span class="sxs-lookup"><span data-stu-id="e1069-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1069-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="e1069-108">Requirements</span></span>  
 <span data-ttu-id="e1069-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1069-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1069-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e1069-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1069-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1069-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1069-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1069-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1069-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1069-113">See also</span></span>

- [<span data-ttu-id="e1069-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e1069-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e1069-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e1069-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
