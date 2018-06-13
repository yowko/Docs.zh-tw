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
ms.openlocfilehash: e22cf8e540bfdb53ad243640dac110b5750e53e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449117"
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
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypeDef`語彙基元，指定要配置的類別。  
  
 `dwPackSize`  
 [in]封裝大小： 1、 2、 4、 8 或 16 個位元組。 封裝大小是相鄰的欄位之間的位元組數。  
  
 `rFieldOffsets`  
 [in]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構，每個皆指定類別的欄位和欄位的位移在類別中。 終止與陣列`mdTokenNil`。  
  
 `ulClassSize`  
 [in]以位元組為單位，類別的大小。  
  
## <a name="remarks"></a>備註  
 藉由呼叫一開始定義類別[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法，並指定其中三個類別的欄位配置： 自動、 循序或明確。 一般來說，您會使用自動配置，讓執行階段選擇欄位配置的最佳方式。  
  
 不過，您可以根據 unmanaged 程式碼使用的排列方式配置的欄位。 在此情況下，選擇 循序或明確的配置和呼叫`SetClassLayout`完成欄位的配置：  
  
-   循序配置： 指定的封裝大小。 欄位會根據其自然的大小或封裝大小，較小的欄位位移中的任何結果對齊。 設定`rFieldOffsets`和`ulClassSize`為零。  
  
-   明確的配置： 指定每個欄位的位移，或指定類別和封裝大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
