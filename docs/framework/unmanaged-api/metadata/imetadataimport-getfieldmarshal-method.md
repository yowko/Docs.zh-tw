---
title: IMetaDataImport::GetFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: 1a4f7703536bcfdae75b0bcffae8dca0734e9e0f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437573"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="2e86e-102">IMetaDataImport::GetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="2e86e-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="2e86e-103">取得指定欄位元資料標記所代表之欄位的原生非受控類型指標。</span><span class="sxs-lookup"><span data-stu-id="2e86e-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e86e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e86e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e86e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e86e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2e86e-106">在元資料標記，表示要取得其 interop 封送處理資訊的欄位。</span><span class="sxs-lookup"><span data-stu-id="2e86e-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="2e86e-107">脫銷欄位的原生類型之中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="2e86e-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="2e86e-108">脫銷`ppvNativeType`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2e86e-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e86e-109">需求</span><span class="sxs-lookup"><span data-stu-id="2e86e-109">Requirements</span></span>  
 <span data-ttu-id="2e86e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e86e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e86e-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2e86e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e86e-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2e86e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e86e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e86e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e86e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e86e-114">See also</span></span>

- [<span data-ttu-id="2e86e-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2e86e-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2e86e-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2e86e-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
