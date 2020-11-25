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
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729209"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA 方法

取得 (RVA) 的相對虛擬位址，以及指定標記所代表之方法或欄位的實旗標。  
  
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
 在MethodDef 或 FieldDef 元資料標記，代表要傳回 RVA 的程式碼物件。 如果 token 是 FieldDef，則欄位必須是全域變數。  
  
 `pulCodeRVA`  
 擴展標記所代表之程式碼物件的相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 擴展方法之實旗標的指標。 這個值是 [CorMethodImpl](cormethodimpl-enumeration.md) 列舉的位元遮罩。 `pdwImplFlags`只有當是 MethodDef 標記時，的值才有效 `tk` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
