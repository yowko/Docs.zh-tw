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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175378"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps 方法
獲取實現指定方法的 的 中繼資料<xref:System.Type>權杖以及聲明該方法的介面的指標。
  
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
 [在]表示要返回類和介面權杖的方法的中繼資料權杖。  
  
 `pClass`  
 [出]表示實現方法的類的中繼資料權杖。  
  
 `ptkIface`  
 [出]表示定義已實現方法的介面的中繼資料權杖。  

## <a name="remarks"></a>備註

 通過調用`iImpl`[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法，可以獲取 的值。

 例如，假設一個類的`mdTypeDef`權杖值為 0x02000007，並且它實現了三個介面，其類型具有權杖：

- 0x0200003 （類型定義）
- 0x0100000A （類型參考）
- 0x0200001C （類型定義）

從概念上講，此資訊存儲在介面實現表中，如：

| 行號 | 類權杖 | 介面權杖 |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

回想，權杖是 4 位元組的值：

- 較低的 3 個位元組保留行號或 RID。
- 上位元組保存的權杖類型 = 0x09。 `mdtInterfaceImpl`

`GetInterfaceImplProps`返回您在`iImpl`參數中提供的權杖行中持有的資訊。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
