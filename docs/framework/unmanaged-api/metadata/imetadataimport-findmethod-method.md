---
title: IMetaDataImport::FindMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177256"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法
獲取指向方法的指標，該方法由指定內容<xref:System.Type>封閉，並且具有指定的名稱和中繼資料簽名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]包含`mdTypeDef`要搜索的成員的類型（類或介面）的權杖。 如果此值為`mdTokenNil`，則對全域函數執行查找。  
  
 `szName`  
 [在]要搜索的方法的名稱。  
  
 `pvSigBlob`  
 [在]指向方法的二進位中繼資料簽名的指標。  
  
 `cbSigBlob`  
 [在]的大小（以位元組為單位）。 `pvSigBlob`  
  
 `pmb`  
 [出]指向匹配的 MethodDef 權杖的指標。  
  
## <a name="remarks"></a>備註  
 使用其封閉類或介面 （））`td``szName`和可選方式指定方法的簽名 （）。`pvSigBlob` 類或介面中可能有多個同名方法。 在這種情況下，傳遞方法的簽名以查找唯一匹配項。  
  
 傳遞給的簽名`FindMethod`必須在當前作用域中生成，因為簽名綁定到特定作用域。 簽名可以嵌入標識封閉類或數值型別的權杖。 權杖是本地 TypeDef 表中的索引。 不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為輸入 到`FindMethod`的輸入。  
  
 `FindMethod`僅查找直接在類或介面中定義的方法;它找不到繼承的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
