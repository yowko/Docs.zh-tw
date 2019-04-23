---
title: IMetaDataImport::GetInterfaceImplProps 方法
ms.date: 02/25/2019
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76e2ebbd47a5e36a722fce33ba67d7efb4db8675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115930"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps 方法
取得中繼資料語彙基元的指標<xref:System.Type>實作指定的方法和介面宣告該方法。
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>參數  
 `iiImpl`  
 [in]中繼資料語彙基元，代表這個方法傳回的類別和介面 token。  
  
 `pClass`  
 [out]中繼資料語彙基元，表示實作方法的類別。  
  
 `ptkIface`  
 [out]中繼資料語彙基元，代表定義的實作的方法的介面。  

## <a name="remarks"></a>備註

 取得值，如`iImpl`藉由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法。
 
 例如，假設 的類別有`mdTypeDef`k 0x02000007 的值，它會實作它的型別具有權杖的三個介面： 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

就概念而言，這項資訊會儲存至介面實作資料表為：

| 資料列數目 | 類別的語彙基元 | 介面的語彙基元 |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

請記住，此語彙基元是 4 位元組值：

- 較低的 3 個位元組會保存資料列數目，或 RID。
- 上方的位元組會保存語彙基元的型別 – 為 0x09 `mdtInterfaceImpl`。

`GetInterfaceImplProps` 傳回的資訊保留在資料列中提供的語彙基元`iImpl`引數。 
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
