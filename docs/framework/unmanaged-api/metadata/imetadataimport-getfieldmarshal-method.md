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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 837b2142e200e224fe32c2c673be0f317633452a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445354"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="a94ce-102">IMetaDataImport::GetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="a94ce-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="a94ce-103">取得指定的欄位中繼資料語彙基元所代表欄位的原生 unmanaged 類型指標。</span><span class="sxs-lookup"><span data-stu-id="a94ce-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a94ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="a94ce-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a94ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="a94ce-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a94ce-106">[in]代表要取得 interop 封送處理資訊的欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a94ce-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="a94ce-107">[out]中繼資料簽章之欄位的原生類型的指標。</span><span class="sxs-lookup"><span data-stu-id="a94ce-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="a94ce-108">[out]以位元組為單位的大小`ppvNativeType`。</span><span class="sxs-lookup"><span data-stu-id="a94ce-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a94ce-109">需求</span><span class="sxs-lookup"><span data-stu-id="a94ce-109">Requirements</span></span>  
 <span data-ttu-id="a94ce-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a94ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a94ce-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a94ce-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a94ce-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a94ce-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a94ce-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a94ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a94ce-114">See Also</span></span>  
 [<span data-ttu-id="a94ce-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a94ce-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a94ce-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a94ce-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
