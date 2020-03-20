---
title: IMetaDataImport::FindMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175417"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef 方法
獲取指向成員參考的指向成員Ref 權杖的指標，該引用由指定內容<xref:System.Type>所封閉，並且具有指定的名稱和中繼資料簽名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]包含要搜索的成員引用的類或介面的 TypeRef 權杖。 如果此值為`mdTokenNil`，則查找將執行全域變數或全域函數引用。  
  
 `szName`  
 [在]要搜索的成員引用的名稱。  
  
 `pvSigBlob`  
 [在]指向成員引用的二進位中繼資料簽名的指標。  
  
 `cbSigBlob`  
 [在]的大小（以位元組為單位）。 `pvSigBlob`  
  
 `pmr`  
 [出]指向匹配的會員Ref權杖的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其封閉類或介面 （））`td``szName`指定成員，並選擇其簽名 （）。`pvSigBlob`  
  
 傳遞給的簽名`FindMemberRef`必須在當前作用域中生成，因為簽名綁定到特定作用域。 簽名可以嵌入標識封閉類或數值型別的權杖。 權杖是本地 TypeDef 表中的索引。 不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為 輸入`FindMemberRef`。  
  
 `FindMemberRef`僅查找直接在類或介面中定義的成員引用;它找不到繼承的成員引用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
