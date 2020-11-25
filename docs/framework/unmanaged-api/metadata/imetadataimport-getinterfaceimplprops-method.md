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
ms.openlocfilehash: e81816ce2194c2c1862cb997ad2c6e5baf301231
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703993"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps 方法

取得的元資料標記指標，該指標 <xref:System.Type> 會執行指定的方法以及宣告該方法的介面。
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>參數  

 `iiImpl`  
 在元資料標記，代表傳回類別和介面標記的方法。  
  
 `pClass`  
 擴展元資料標記，代表實方法的類別。  
  
 `ptkIface`  
 擴展元資料標記，代表定義已執行方法的介面。  

## <a name="remarks"></a>備註

 您可以藉 `iImpl` 由呼叫 [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) 方法來取得的值。

 例如，假設某個類別具有 `mdTypeDef` 0x02000007 的 token 值，且它會執行類型具有權杖的三個介面：

- 0x02000003 (TypeDef) 
- 0x0100000A (TypeRef) 
- 0x0200001C (TypeDef) 

就概念而言，此資訊會儲存在介面實資料表中，如下所示：

| 資料列編號 | 類別 token | 介面 token |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

回想一下，權杖是4個位元組的值：

- 較低的3個位元組會保存資料列編號或 RID。
- 上層位元組保留的 token 類型– 0x09 `mdtInterfaceImpl` 。

`GetInterfaceImplProps` 傳回資料列中所保留的資訊，您在引數中提供的權杖 `iImpl` 。
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
