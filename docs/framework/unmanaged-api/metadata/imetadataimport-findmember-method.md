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
ms.openlocfilehash: bcd9499d0aef34fb34065ed58c0f0d69cc4ecedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711438"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember 方法

取得欄位或方法的 MemberDef token 指標，這個欄位或方法是由指定的 <xref:System.Type> ，且具有指定的名稱和中繼資料簽章。  
  
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
 在包含要搜尋之成員之類別或介面的 TypeDef 標記。 如果這個值為 `mdTokenNil` ，則會對全域變數或全域函式進行查閱。  
  
 `szName`  
 在要搜尋之成員的名稱。  
  
 `pvSigBlob`  
 在成員的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmb`  
 擴展相符 MemberDef token 的指標。  
  
## <a name="remarks"></a>備註  

 您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定成員 `pvSigBlob` 。 類別或介面中可能有多個相同名稱的成員。 在此情況下，請傳遞成員的簽章，以找出唯一的相符項。  
  
 傳遞給的簽章 `FindMember` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。 簽章可以內嵌可識別封閉類別或實數值型別的標記。 Token 是本機 TypeDef 資料表中的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入的輸入 `FindMember` 。  
  
 `FindMember` 只尋找直接定義于類別或介面中的成員;找不到繼承的成員。  
  
> [!NOTE]
> `FindMember` 是 helper 方法。 它會呼叫 [IMetaDataImport：： FindMethod](imetadataimport-findmethod-method.md);如果該呼叫找不到相符的， `FindMember` 則會呼叫 [IMetaDataImport：： FindField](imetadataimport-findfield-method.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
