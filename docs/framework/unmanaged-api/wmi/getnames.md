---
title: 'GetNames 函式 (非受控 API 參考) '
description: GetNames 函式會抓取物件的屬性名稱。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687654"
---
# <a name="getnames-function"></a>GetNames 函式

擷取物件屬性的子集合或所有名稱。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a>參數

`vFunc`  
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`wszQualifierName`  
在有效的指標， `LPCWSTR` 指定做為篩選準則一部分運作的辨識符號名稱。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。 這個參數可以是 `null`。

`lFlags`  
在位欄位的組合。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。

`pQualifierValue` 在有效結構的指標，此 `VARIANT` 結構會初始化為篩選值。 這個參數可以是 `null`。

`pstrNames`  
擴展 `SAFEARRAY` 包含屬性名稱的結構。 在輸入時，這個參數必須一律為的指標 `null` 。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效，或指定了不正確的旗標和參數組合。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) 方法的呼叫。

命名傳回的會由旗標和參數的組合來控制。 例如，函數可以傳回所有屬性的名稱，或只傳回索引鍵屬性的名稱。  主要篩選準則是在參數中指定 `lFlags` ，而其他參數則會根據它而有所不同。

中的旗標值 `lFlags` 為位欄位

可以做為引數傳遞的旗 `lEnumFlags` 標是 *WbemCli .h* 標頭檔中定義的位欄位，您也可以在程式碼中將它們定義為常數。  您可以結合每個群組中的一個旗標與任何其他群組的任何旗標。 不過，來自相同群組的旗標是互斥的。

| 群組1旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | 傳回所有屬性名稱。 `strQualifierName` 和 `pQualifierVal` 都未使用。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 只傳回具有參數所指定名稱之限定詞的屬性 `strQualifierName` 。 如果使用此旗標，您必須指定 `strQualifierName` 。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  只傳回沒有參數所指定名稱之限定詞的屬性 `strQualifierName` 。 如果使用此旗標，您必須指定 `strQualifierName` 。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | 只傳回具有參數所指定名稱之限定詞的屬性 `wszQualifierName` ，而且其值與結構所指定的值相同 `pQualifierVal` 。 如果使用此旗標，您必須同時指定 `wszQualifierName` 和 `pQualifierValue` 。 |

| 群組2旗標 |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 只傳回定義索引鍵之屬性的名稱。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 只傳回物件參考的屬性名稱。 |

| 群組3旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 只傳回屬於最衍生類別的屬性名稱。 排除父類別的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 只傳回屬於父類別的屬性名稱。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 只傳回系統屬性的名稱。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 只傳回非系統屬性的名稱。 |

函式一律會在傳回時配置新的 `SAFEARRAY` `WBEM_S_NO_ERROR` ，而且 `pstrNames` 一律設定為指向它。 如果沒有屬性符合指定的篩選準則，則傳回的陣列可以有0個元素。 如果函數傳回以外的值 `WBM_S_NO_ERROR` ， `SAFEARRAY` 則不會傳回新的結構。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
