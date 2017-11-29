---
title: "IMetaDataImport::GetInterfaceImplProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetInterfaceImplProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0843c9823ba40944e6ea075d469f9a76510d8714
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="be555-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="be555-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="be555-103">取得中繼資料語彙基元的指標<xref:System.Type>會實作指定的方法，並以介面宣告該方法。</span><span class="sxs-lookup"><span data-stu-id="be555-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be555-104">語法</span><span class="sxs-lookup"><span data-stu-id="be555-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be555-105">參數</span><span class="sxs-lookup"><span data-stu-id="be555-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="be555-106">[in]中繼資料語彙基元，代表這個方法傳回的類別和介面 token。</span><span class="sxs-lookup"><span data-stu-id="be555-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="be555-107">[out]中繼資料語彙基元，代表實作方法的類別。</span><span class="sxs-lookup"><span data-stu-id="be555-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="be555-108">[out]中繼資料語彙基元，代表定義的實作的方法的介面。</span><span class="sxs-lookup"><span data-stu-id="be555-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be555-109">需求</span><span class="sxs-lookup"><span data-stu-id="be555-109">Requirements</span></span>  
 <span data-ttu-id="be555-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be555-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be555-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be555-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be555-112">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="be555-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be555-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be555-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be555-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be555-114">See Also</span></span>  
 [<span data-ttu-id="be555-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="be555-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="be555-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="be555-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
