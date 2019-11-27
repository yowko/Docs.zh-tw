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
ms.openlocfilehash: 205f48fb417365565695c72095187d349127e536
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436858"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="01e4f-102">IMetaDataImport::GetSigFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="01e4f-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="01e4f-103">取得與指定語彙基元相關聯的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="01e4f-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="01e4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e4f-105">參數</span><span class="sxs-lookup"><span data-stu-id="01e4f-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="01e4f-106">在要為其傳回二進位中繼資料簽章的 token。</span><span class="sxs-lookup"><span data-stu-id="01e4f-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="01e4f-107">脫銷傳回之中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="01e4f-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="01e4f-108">脫銷二進位中繼資料簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="01e4f-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e4f-109">需求</span><span class="sxs-lookup"><span data-stu-id="01e4f-109">Requirements</span></span>  
 <span data-ttu-id="01e4f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01e4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e4f-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="01e4f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01e4f-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01e4f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01e4f-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e4f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01e4f-114">See also</span></span>

- [<span data-ttu-id="01e4f-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="01e4f-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="01e4f-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="01e4f-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
