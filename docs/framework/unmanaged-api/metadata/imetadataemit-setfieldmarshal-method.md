---
title: "IMetaDataEmit::SetFieldMarshal 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3ef1d50d0d74a92a5bcaf23981226e5a6c852edd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="dbc53-102">IMetaDataEmit::SetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="dbc53-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="dbc53-103">設定的 PInvoke 封送處理指定的語彙基元所參考的欄位、 return、 方法或方法參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="dbc53-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc53-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbc53-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbc53-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbc53-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dbc53-106">[in]目標資料的項目之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dbc53-106">[in] The token for target data item.</span></span> <span data-ttu-id="dbc53-107">這可能是`mdFieldDef`或`mdParamDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dbc53-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="dbc53-108">[in]Unmanaged 類型的簽章。</span><span class="sxs-lookup"><span data-stu-id="dbc53-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="dbc53-109">[in]中的位元組計數`pvNativeType`。</span><span class="sxs-lookup"><span data-stu-id="dbc53-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc53-110">需求</span><span class="sxs-lookup"><span data-stu-id="dbc53-110">Requirements</span></span>  
 <span data-ttu-id="dbc53-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc53-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc53-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dbc53-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbc53-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dbc53-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbc53-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc53-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc53-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc53-115">See Also</span></span>  
 [<span data-ttu-id="dbc53-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="dbc53-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dbc53-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="dbc53-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
