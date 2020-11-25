---
title: 'GetObjectText 函式 (非受控 API 參考) '
description: GetObjectText 函式會以 MOF 語法傳回物件的文字呈現。
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
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718367"
---
# <a name="getobjecttext-function"></a>GetObjectText 函式

以受控物件格式 (MOF) 語法傳回物件的文字呈現。

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
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`lFlags`  
在通常是0。 如果 `WBEM_FLAG_NO_FLAVORS` 指定了 (或 0x1) ，則不會包含任何傳播或類別資訊的限定詞。

`pstrObjectText` 擴展On 專案的指標 `null` 。 傳回時，為新配置 `BSTR` 的，包含物件的 MOF 語法轉譯。  

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) 方法的呼叫。

傳回的 MOF 文字未包含物件的所有相關資訊，但只有足夠的資訊可讓 MOF 編譯器能夠重新建立原始物件。 例如，不包含任何傳播的限定詞或父類別屬性。

下列演算法用來重建方法參數的文字：

1. 參數的 resequenced 順序為其識別碼值。
1. 以和指定的參數 `[in]` `[out]` 會結合為單一參數。

`pstrObjectText` 當呼叫函式時，必須是指向的指標 `null` ; 因為指標不會解除配置，所以它不能指向方法呼叫之前的有效字串。

## <a name="requirements"></a>需求  

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
