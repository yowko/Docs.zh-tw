---
title: GetObjectText 函式（非受控 API 參考）
description: GetObjectText 函數會以 MOF 語法傳回物件的文字呈現。
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
ms.openlocfilehash: d47fcd59204a4d114fc9f0dc5bc4550ba1681f33
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798501"
---
# <a name="getobjecttext-function"></a>GetObjectText 函式
以受控物件格式（MOF）語法傳回物件的文字呈現。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
在未使用此參數。

`ptr`  
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`lFlags`  
在通常是0。 如果`WBEM_FLAG_NO_FLAVORS`指定（或0x1），則會包含不含傳播或類別資訊的限定詞。

`pstrObjectText`   
脫銷`null` On 專案的指標。 傳回時，是新`BSTR`配置的，其中包含物件的 MOF 語法呈現。  

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法的呼叫。

傳回的 MOF 文字未包含物件的所有相關資訊，但 MOF 編譯器只有足夠的資訊可以重新建立原始物件。 例如，未包含任何傳播的限定詞或父類別屬性。

下列演算法是用來重建方法的參數文字：

1. 參數是以其識別碼值的順序 resequenced。
1. 指定為`[in]`和`[out]`的參數會結合成單一參數。
 
`pstrObjectText`呼叫函式`null`時，必須是的指標，而且不能指向方法呼叫之前的有效字串，因為指標將不會解除配置。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
