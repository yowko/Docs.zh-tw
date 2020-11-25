---
title: 'QualifierSet_Get 函式 (非受控 API 參考) '
description: QualifierSet_Get 函式會取得命名限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd096287b85b4a51a8cae85dddcca95cc1a8dbae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721136"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get 函式

取得指定的具名限定詞。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>參數

`vFunc` 在此參數未使用。

`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。

`wszName` 在要求其值的辨識符號名稱。

`lFlags` 在保留。 此參數必須為0。

`pVal` 擴展如果成功，則為辨識符號的正確類型和值。 如果函式失敗，則 `VARIANT` `pVal` 不會修改指向的。 如果此參數為 `null` ，則會忽略參數。

`plFlavor` 擴展LONG 的指標，可接收所要求限定詞的限定詞類別位。 如果不需要類別資訊，這個參數可以是 `null` 。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定的限定詞不存在。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemQualifierSet：： Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) 方法的呼叫。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
