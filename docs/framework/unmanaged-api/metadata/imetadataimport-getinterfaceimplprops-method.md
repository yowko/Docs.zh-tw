---
title: "IMetaDataImport::GetInterfaceImplProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: afc73536f332bd24fadee33d6321a106ccd175f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="250fc-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="250fc-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="250fc-103">取得中繼資料語彙基元的指標<xref:System.Type>會實作指定的方法，並以介面宣告該方法。</span><span class="sxs-lookup"><span data-stu-id="250fc-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="250fc-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="250fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="250fc-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="250fc-106">[in]中繼資料語彙基元，代表這個方法傳回的類別和介面 token。</span><span class="sxs-lookup"><span data-stu-id="250fc-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="250fc-107">[out]中繼資料語彙基元，代表實作方法的類別。</span><span class="sxs-lookup"><span data-stu-id="250fc-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="250fc-108">[out]中繼資料語彙基元，代表定義的實作的方法的介面。</span><span class="sxs-lookup"><span data-stu-id="250fc-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250fc-109">需求</span><span class="sxs-lookup"><span data-stu-id="250fc-109">Requirements</span></span>  
 <span data-ttu-id="250fc-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="250fc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250fc-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="250fc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="250fc-112">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="250fc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="250fc-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250fc-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="250fc-114">See Also</span></span>  
 [<span data-ttu-id="250fc-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="250fc-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="250fc-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="250fc-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
