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
ms.openlocfilehash: 62495aa4280bb1799af09fea2e550ae6107e09e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729144"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="6dc14-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="6dc14-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="6dc14-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="6dc14-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc14-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dc14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dc14-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dc14-105">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="6dc14-106">在與要求的中繼資料簽章相關聯的 TypeSpec token。</span><span class="sxs-lookup"><span data-stu-id="6dc14-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="6dc14-107">擴展二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="6dc14-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="6dc14-108">擴展中繼資料簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6dc14-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dc14-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dc14-109">Return Value</span></span>  

 <span data-ttu-id="6dc14-110">表示成功或失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6dc14-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="6dc14-111">您可以使用失敗的宏來測試失敗。</span><span class="sxs-lookup"><span data-stu-id="6dc14-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc14-112">需求</span><span class="sxs-lookup"><span data-stu-id="6dc14-112">Requirements</span></span>  

 <span data-ttu-id="6dc14-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dc14-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dc14-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6dc14-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dc14-115">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6dc14-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6dc14-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc14-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc14-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dc14-117">See also</span></span>

- [<span data-ttu-id="6dc14-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6dc14-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6dc14-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6dc14-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
