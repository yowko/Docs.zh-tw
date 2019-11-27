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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441773"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout 方法
完成先前呼叫[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)所定義之類別的欄位版面配置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 在`mdTypeDef` token，指定要配置的類別。  
  
 `dwPackSize`  
 在封裝大小：1、2、4、8或16個位元組。 封裝大小是相鄰欄位之間的位元組數目。  
  
 `rFieldOffsets`  
 在[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構的陣列，其中每一個都會指定類別的欄位，以及類別內的欄位位移。 使用 `mdTokenNil`終止陣列。  
  
 `ulClassSize`  
 在類別的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 此類別一開始是藉由呼叫[IMetaDataEmit：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法來定義，並為類別的欄位指定三個配置的其中一個：自動、連續或明確。 一般來說，您會使用自動版面配置，並讓執行時間選擇配置欄位的最佳方式。  
  
 不過，您可能會想要根據非受控碼所使用的相片順序來配置欄位。 在此情況下，請選擇 [連續] 或 [明確配置]，並呼叫 `SetClassLayout` 來完成欄位的版面配置：  
  
- 連續版面配置：指定封裝大小。 欄位會根據其自然大小或封裝大小來對齊，以較小的方式產生欄位的位移。 將 `rFieldOffsets` 和 `ulClassSize` 設定為零。  
  
- 明確配置：指定每個欄位的位移，或指定類別大小和封裝大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
