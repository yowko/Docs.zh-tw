---
title: IMetaDataImport::GetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 58ab9ee9381fce4d7af1910df6c8d3bb813bcf13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490887"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA 方法
取得指定標記所代表之方法或欄位的相對虛擬位址（RVA）和執行旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在MethodDef 或 FieldDef 元資料標記，代表要為其傳回 RVA 的程式碼物件。 如果權杖是 FieldDef，此欄位必須是全域變數。  
  
 `pulCodeRVA`  
 脫銷標記所表示之程式碼物件的相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 脫銷方法之執行旗標的指標。 這個值是[CorMethodImpl](cormethodimpl-enumeration.md)列舉中的位元遮罩。 `pdwImplFlags`只有當是 MethodDef token 時，的值才有效 `tk` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
