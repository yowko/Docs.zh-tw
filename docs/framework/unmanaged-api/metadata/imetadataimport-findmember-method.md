---
title: IMetaDataImport::FindMember 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177274"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember 方法
獲取指向成員Def權杖的指標，用於指定<xref:System.Type>內容所包含且具有指定名稱和中繼資料簽名的欄位或方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]包含要搜索的成員的類或介面的 TypeDef 權杖。 如果此值為`mdTokenNil`，則查找將執行全域變數或全域函數。  
  
 `szName`  
 [在]要搜索的成員的名稱。  
  
 `pvSigBlob`  
 [在]指向成員的二進位中繼資料簽名的指標。  
  
 `cbSigBlob`  
 [在]的大小（以位元組為單位）。 `pvSigBlob`  
  
 `pmb`  
 [出]指向匹配的會員Def權杖的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其封閉類或介面 （））`td``szName`指定成員，並選擇其簽名 （）。`pvSigBlob` 類或介面中可能有多個具有相同名稱的成員。 在這種情況下，傳遞成員的簽名以查找唯一匹配項。  
  
 傳遞給的簽名`FindMember`必須在當前作用域中生成，因為簽名綁定到特定作用域。 簽名可以嵌入標識封閉類或數值型別的權杖。 權杖是本地 TypeDef 表中的索引。 不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為輸入 到`FindMember`的輸入。  
  
 `FindMember`僅查找直接在類或介面中定義的成員;它找不到繼承的成員。  
  
> [!NOTE]
> `FindMember`是説明方法。 它調用[IMetaData 導入：：查找方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md);如果該呼叫找不到匹配項，`FindMember`則調用[IMetaDataImport：：FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
