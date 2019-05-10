---
title: IMetaDataEmit::SetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28eb8124d201f474ac8029a4c2b8a908755d6f8e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584664"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout 方法
完成欄位已由先前呼叫所定義之類別的配置[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypeDef`語彙基元，指定要配置的類別。  
  
 `dwPackSize`  
 [in]封裝大小：1、 2、 4、 8 或 16 個位元組。 封裝大小是相鄰的欄位之間的位元組數目。  
  
 `rFieldOffsets`  
 [in]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構，其中每一個指定類別的欄位和欄位之間的時差，該類別內。 終止陣列`mdTokenNil`。  
  
 `ulClassSize`  
 [in]大小，以位元組為單位的類別。  
  
## <a name="remarks"></a>備註  
 一開始已定義類別，藉由呼叫[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法，並指定其中一個欄位的類別的三個配置： 自動、 循序或明確。 一般來說，您會使用自動版面配置，並讓執行階段選擇最佳的方式來配置的欄位。  
  
 不過，您可以根據程式碼會使用未受管理的排列方式配置的欄位。 在此情況下，選擇 循序或明確的配置和呼叫`SetClassLayout`完成欄位的配置：  
  
- 循序配置：指定封裝大小。 欄位會根據其自然的大小或封裝大小，任何會導致較小的欄位位移對齊。 設定`rFieldOffsets`和`ulClassSize`為零。  
  
- 明確的配置：指定每個欄位的位移，或指定類別和封裝大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
