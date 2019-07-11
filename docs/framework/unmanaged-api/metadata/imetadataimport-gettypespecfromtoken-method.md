---
title: IMetaDataImport::GetTypeSpecFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7e060d2f72609b470dbd5060746a1458f5eed9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782303"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="8eaca-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="8eaca-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="8eaca-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="8eaca-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eaca-104">語法</span><span class="sxs-lookup"><span data-stu-id="8eaca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eaca-105">參數</span><span class="sxs-lookup"><span data-stu-id="8eaca-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="8eaca-106">[in]要求的中繼資料簽章相關聯的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8eaca-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="8eaca-107">[out]二進位的中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="8eaca-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="8eaca-108">[out]大小，以位元組為單位的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="8eaca-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8eaca-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8eaca-109">Return Value</span></span>  
 <span data-ttu-id="8eaca-110">指出成功或失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8eaca-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="8eaca-111">使用 FAILED 巨集，您可以測試失敗。</span><span class="sxs-lookup"><span data-stu-id="8eaca-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eaca-112">需求</span><span class="sxs-lookup"><span data-stu-id="8eaca-112">Requirements</span></span>  
 <span data-ttu-id="8eaca-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8eaca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eaca-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8eaca-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8eaca-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8eaca-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8eaca-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eaca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eaca-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eaca-117">See also</span></span>

- [<span data-ttu-id="8eaca-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8eaca-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8eaca-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8eaca-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
