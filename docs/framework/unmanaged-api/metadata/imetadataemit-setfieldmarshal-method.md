---
title: IMetaDataEmit::SetFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82675af85f049aeb288b3dcc18f222c0387a37b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150393"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="22258-102">IMetaDataEmit::SetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="22258-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="22258-103">設定的 PInvoke 封送處理指定的語彙基元所參考的欄位、 return、 方法或方法參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="22258-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22258-104">語法</span><span class="sxs-lookup"><span data-stu-id="22258-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22258-105">參數</span><span class="sxs-lookup"><span data-stu-id="22258-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="22258-106">[in]目標資料的項目之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="22258-106">[in] The token for target data item.</span></span> <span data-ttu-id="22258-107">這是`mdFieldDef`或`mdParamDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="22258-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="22258-108">[in]Unmanaged 類型簽章。</span><span class="sxs-lookup"><span data-stu-id="22258-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="22258-109">[in]中的位元組計數`pvNativeType`。</span><span class="sxs-lookup"><span data-stu-id="22258-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22258-110">需求</span><span class="sxs-lookup"><span data-stu-id="22258-110">Requirements</span></span>  
 <span data-ttu-id="22258-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22258-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22258-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22258-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22258-113">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="22258-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="22258-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="22258-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22258-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22258-115">See also</span></span>

- [<span data-ttu-id="22258-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="22258-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="22258-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="22258-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
