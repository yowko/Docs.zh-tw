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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177565"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout 方法
完成由之前調用[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)定義的類的欄位佈局。  
  
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
 [在]指定`mdTypeDef`要佈局的類的權杖。  
  
 `dwPackSize`  
 [在]包裝尺寸：1、2、4、8 或 16 位元組。 包裝大小是相鄰欄位之間的位元組數。  
  
 `rFieldOffsets`  
 [在][COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構陣列，每個結構指定類的欄位和類中的欄位偏移量。 使用 終止陣列`mdTokenNil`。  
  
 `ulClassSize`  
 [在]類的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 類最初通過調用[IMetaDataEmit：:DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法來定義，並為類的欄位指定三個佈局之一：自動、順序或顯式。 通常，您將使用自動佈局，讓運行時選擇佈局欄位的最佳方式。  
  
 但是，您可能希望根據非託管代碼使用的相片順序佈局欄位。 在這種情況下，選擇順序或顯式佈局並調用`SetClassLayout`以完成欄位的佈局：  
  
- 順序佈局：指定包裝大小。 欄位根據其自然大小或包裝大小對齊，以導致欄位偏移較小的為准。 設置`rFieldOffsets`和`ulClassSize`零。  
  
- 顯式佈局：指定每個欄位的偏移量或指定類大小和包裝大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
