---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0777151d10149ec7311a7761bc7f6bff5ba98e0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777482"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法
建立 common language runtime 型別中，型別定義，並取得該型別定義的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>參數  
 `szTypeDef`  
 [in]以 Unicode 的型別名稱。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`屬性。 這是位元遮罩`CoreTypeAttr`值。  
  
 `tkExtends`  
 [in]基底類別的語彙基元。 它必須是`mdTypeDef`或`mdTypeRef`語彙基元。  
  
 `rtkImplements`  
 [in]指定此類別或介面實作的介面的語彙基元的陣列。  
  
 `ptd`  
 [out]`mdTypeDef`指派權杖。  
  
## <a name="remarks"></a>備註  
 中的旗標`dwTypeDefFlags`指定所建立的型別是否為一般類型系統參考類型 （類別或介面） 或一般類型系統實值型別。  
  
 根據提供的參數，此方法中，副作用，也可以建立`mdInterfaceImpl`記錄每個介面都是繼承，或由此類型實作。 不過，這個方法不會傳回任何一項都`mdInterfaceImpl`語彙基元。 如果用戶端想要稍後再新增或修改`mdInterfaceImpl`語彙基元，必須使用`IMetaDataImport`加以列舉的介面。 如果您想要使用的 COM 語意`[default]`介面，您應該提供的預設介面中的第一個元素`rtkImplements`; 在類別上設定的自訂屬性會指出類別有一個預設介面 (這一律假定為第一次`mdInterfaceImpl`類別宣告的權杖)。  
  
 每個項目的`rtkImplements`陣列保留`mdTypeDef`或`mdTypeRef`語彙基元。 陣列中的最後一個項目必須是`mdTokenNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
