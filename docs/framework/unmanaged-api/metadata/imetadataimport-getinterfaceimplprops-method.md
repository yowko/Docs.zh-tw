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
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437546"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps 方法
取得執行指定方法之 <xref:System.Type> 的元資料標記指標，以及宣告該方法之介面的指標。
  
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
 在元資料標記，代表要傳回其類別和介面標記的方法。  
  
 `pClass`  
 脫銷元資料標記，代表可執行方法的類別。  
  
 `ptkIface`  
 脫銷元資料標記，代表定義已執行之方法的介面。  

## <a name="remarks"></a>備註

 您可以藉由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法來取得 `iImpl` 的值。
 
 例如，假設類別具有0x02000007 的 `mdTypeDef` token 值，而且它會實作為類型具有權杖的三個介面： 

- 0x02000003 （TypeDef）
- 0x0100000A （TypeRef）
- 0x0200001C （TypeDef）

就概念而言，這種資訊會儲存在介面執行資料表中，如下所示：

| 資料列編號 | 類別 token | 介面 token |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

回想一下，權杖是4個位元組的值：

- 較低的3個位元組會保存資料列編號或 RID。
- 大小上限會保存 `mdtInterfaceImpl`的 token 類型-0x09。

`GetInterfaceImplProps` 會傳回您在 `iImpl` 引數中提供之權杖的資料列中所保存的資訊。 
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
