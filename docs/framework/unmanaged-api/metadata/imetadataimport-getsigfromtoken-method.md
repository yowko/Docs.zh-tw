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
ms.openlocfilehash: 5af59e158a34b06d304a98db1dfaa46585b22eb6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177200"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="72efb-102">IMetaDataImport::GetSigFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="72efb-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="72efb-103">取得與指定語彙基元相關聯的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="72efb-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72efb-104">語法</span><span class="sxs-lookup"><span data-stu-id="72efb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72efb-105">參數</span><span class="sxs-lookup"><span data-stu-id="72efb-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="72efb-106">[在]要返回的二進位中繼資料簽名的權杖。</span><span class="sxs-lookup"><span data-stu-id="72efb-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="72efb-107">[出]指向返回的中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="72efb-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="72efb-108">[出]二進位中繼資料簽名的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="72efb-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72efb-109">需求</span><span class="sxs-lookup"><span data-stu-id="72efb-109">Requirements</span></span>  
 <span data-ttu-id="72efb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72efb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72efb-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="72efb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72efb-112">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="72efb-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72efb-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72efb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72efb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72efb-114">See also</span></span>

- [<span data-ttu-id="72efb-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="72efb-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="72efb-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="72efb-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
