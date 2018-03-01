---
title: "IMetaDataEmit::DefineTypeDef 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法
建立型別定義為 common language runtime 類型，並取得該型別定義的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szTypeDef`  
 [in]以 Unicode 的型別名稱。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`屬性。 這是位元遮罩`CoreTypeAttr`值。  
  
 `tkExtends`  
 [in]基底類別的語彙基元。 它必須是`mdTypeDef`或`mdTypeRef`語彙基元。  
  
 `rtkImplements`  
 [in]指定此類別或介面實作的介面的語彙基元的陣列。  
  
 `ptd`  
 [out]`mdTypeDef`指派的語彙基元。  
  
## <a name="remarks"></a>備註  
 中的旗標`dwTypeDefFlags`指定正在建立的類型是否為一般類型系統參考類型 （類別或介面） 或一般類型系統實值類型。  
  
 根據提供的參數，這個方法，副作用，也可能會建立`mdInterfaceImpl`記錄每個介面繼承，或由此類型實作。 不過，這個方法不會傳回任何一項都`mdInterfaceImpl`語彙基元。 如果用戶端想要稍後加入或修改`mdInterfaceImpl`語彙基元，必須使用`IMetaDataImport`介面加以列舉。 如果您想要使用的 COM 語意`[default]`介面，您應該提供的預設介面中的第一個項目作為`rtkImplements`; 在類別上設定的自訂屬性會指示此類別具有預設介面 (一律會假設為第一次`mdInterfaceImpl`類別宣告的權杖)。  
  
 每個項目`rtkImplements`陣列保留`mdTypeDef`或`mdTypeRef`語彙基元。 陣列中的最後一個項目必須是`mdTokenNil`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
