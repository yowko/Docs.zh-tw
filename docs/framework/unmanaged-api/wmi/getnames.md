---
title: GetNames 函式（非受控 API 參考）
description: GetNames 函數會抓取物件屬性的名稱。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 748767596a8f4680a2d7b63cb0579acaed5f53f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798521"
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
在未使用此參數。

`ptr`  
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszQualifierName`  
在有效`LPCWSTR`的指標，指定做為篩選準則一部分運作的限定詞名稱。 如需詳細資訊，請參閱[備註](#remarks)一節。 這個參數可以是 `null`。 

`lFlags`  
在位欄位的組合。 如需詳細資訊，請參閱[備註](#remarks)一節。

`pQualifierValue`   
在已初始化為篩選值`VARIANT`之有效結構的指標。 這個參數可以是 `null`。 

`pstrNames`  
脫銷包含屬性名稱的結構。`SAFEARRAY` 在輸入時，這個參數必須一律為的指標`null`。 如需詳細資訊，請參閱[備註](#remarks)一節。 

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效，或指定了不正確的旗標和參數組合。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法的呼叫。

已命名的傳回是由旗標和參數的組合所控制。 例如，函式可以傳回所有屬性的名稱，或只傳回索引鍵屬性的名稱。  主要篩選準則是在`lFlags`參數中指定，而其他參數則會根據它而有所不同。

中`lFlags`的旗標值為位欄位

可當做`lEnumFlags`引數傳遞的旗標是在*WbemCli*標頭檔中定義的位欄位，或者您可以在程式碼中將它們定義為常數。  您可以將每個群組中的一個旗標與任何其他群組中的任何旗標結合。 不過，來自相同群組的旗標是互斥的。 

| 群組1旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | 傳回所有屬性名稱。 `strQualifierName`和`pQualifierVal`未使用。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 只傳回具有`strQualifierName`參數所指定名稱之限定詞的屬性。 如果使用此旗標，您必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  只傳回沒有`strQualifierName`參數所指定名稱之限定詞的屬性。 如果使用此旗標，您必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | 只傳回具有`wszQualifierName`參數所指定名稱之限定詞的屬性，而且其值與結構所`pQualifierVal`指定的值相同。 如果使用這個旗標，您必須同時`wszQualifierName`指定`pQualifierValue`和。 |

| 群組2旗標 |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 只傳回定義索引鍵的屬性名稱。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 只傳回物件參考的屬性名稱。 |

| 群組3旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 只傳回屬於最衍生類別的屬性名稱。 從父類別中排除屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 只傳回屬於父類別的屬性名稱。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 只傳回系統屬性的名稱。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 只傳回非系統屬性的名稱。 |

函式一律會配置新`SAFEARRAY`的`WBEM_S_NO_ERROR`（如果它傳回`pstrNames` ），而且一律會設定為指向它。 如果沒有屬性符合指定的篩選準則，則傳回的陣列可以有0個元素。 如果函數傳回的值`WBM_S_NO_ERROR`不是，則不會傳回新`SAFEARRAY`的結構。
 
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
