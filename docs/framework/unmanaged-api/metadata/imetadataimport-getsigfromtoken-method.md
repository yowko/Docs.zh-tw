---
title: IMetaDataImport::GetSigFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40fb2e94eac13211cf8ccf179904071a23f59ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447223"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="9bcd9-102">IMetaDataImport::GetSigFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="9bcd9-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="9bcd9-103">取得與指定語彙基元相關聯的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="9bcd9-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bcd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="9bcd9-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bcd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="9bcd9-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="9bcd9-106">[in]要傳回的二進位中繼資料簽章的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9bcd9-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="9bcd9-107">[out]傳回的中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="9bcd9-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="9bcd9-108">[out]以位元組為單位的二進位中繼資料簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="9bcd9-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bcd9-109">需求</span><span class="sxs-lookup"><span data-stu-id="9bcd9-109">Requirements</span></span>  
 <span data-ttu-id="9bcd9-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcd9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bcd9-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bcd9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bcd9-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9bcd9-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bcd9-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bcd9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bcd9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bcd9-114">See Also</span></span>  
 [<span data-ttu-id="9bcd9-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9bcd9-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9bcd9-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9bcd9-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
