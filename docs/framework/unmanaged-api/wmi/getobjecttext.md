---
title: GetObjectText 函式 （Unmanaged API 參考）
description: GetObjectText 函式會傳回物件的文字呈現以 MOF 語法。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3a7d606f64dfe1a1abfd3da930fd00957da90a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583573"
---
# <a name="getobjecttext-function"></a>GetObjectText 函式
在受管理物件格式 (MOF) 語法中傳回之物件的文字呈現。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lFlags`  
[in]通常是 0。 如果`WBEM_FLAG_NO_FLAVORS`（或 0x1） 指定，限定詞會包含不含傳播或類別的資訊。

`pstrObjectText`   
[out]指標`null`項目。 傳回時，新配置`BSTR`，其中包含物件的 MOF 語法呈現。  

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法。

傳回的 MOF 文字不包含所有物件的資訊，但僅足夠 MOF 編譯器能夠重新建立原始物件的資訊。 比方說，沒有傳播的限定詞或父類別的內容會包含。

若要重新建構方法的參數的文字使用下列演算法：

1. 參數是以它們的識別碼值順序 resequenced。
1. 為指定的參數`[in]`和`[out]`會結合成單一參數。
 
`pstrObjectText` 必須是指標，`null`時呼叫的函式; 它必須指向是有效的方法呼叫前，因為指標將不會取消配置的字串。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱
- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
