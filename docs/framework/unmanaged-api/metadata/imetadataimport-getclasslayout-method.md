---
title: IMetaDataImport::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175404"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout 方法
取得指定 TypeDef 語彙基元所參考類別的配置資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]要返回佈局的類的 TypeDef 權杖。  
  
 `pdwPackSize`  
 [出]值 1、2、4、8 或 16，表示類的包大小。  
  
 `rFieldOffset`  
 [出][COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)值的陣列。  
  
 `cMax`  
 [in] `rFieldOffset` 陣列的大小上限。  
  
 `pcFieldOffset`  
 [出]中`rFieldOffset`返回的元素數。  
  
 `pulClassSize`  
 [出]以 的類大小（以位元組為單位）。 `td`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
