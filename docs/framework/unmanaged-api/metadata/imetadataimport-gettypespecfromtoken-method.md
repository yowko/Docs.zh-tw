---
title: "IMetaDataImport::GetTypeSpecFromToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37a8c2580dad3e198290b72b49b0aacaf1804c25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="53e83-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="53e83-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="53e83-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="53e83-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e83-104">語法</span><span class="sxs-lookup"><span data-stu-id="53e83-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53e83-105">參數</span><span class="sxs-lookup"><span data-stu-id="53e83-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="53e83-106">[in]要求的中繼資料簽章相關聯的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="53e83-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="53e83-107">[out]指向的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="53e83-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="53e83-108">[out]大小，以位元組為單位的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="53e83-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53e83-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="53e83-109">Return Value</span></span>  
 <span data-ttu-id="53e83-110">指出成功或失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="53e83-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="53e83-111">與 FAILED 巨集，就可以測試失敗。</span><span class="sxs-lookup"><span data-stu-id="53e83-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e83-112">需求</span><span class="sxs-lookup"><span data-stu-id="53e83-112">Requirements</span></span>  
 <span data-ttu-id="53e83-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53e83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e83-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53e83-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53e83-115">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="53e83-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53e83-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e83-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53e83-117">See Also</span></span>  
 [<span data-ttu-id="53e83-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="53e83-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="53e83-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="53e83-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
