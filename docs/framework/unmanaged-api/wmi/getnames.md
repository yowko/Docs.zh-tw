---
title: GetNames 函式 （Unmanaged API 參考）
description: GetNames 函式來擷取物件屬性的名稱。
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
ms.openlocfilehash: f53174bf060938d5a55cbd196944ac11916d59cd
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258107"
---
# <a name="getnames-function"></a>GetNames 函式
擷取部分或所有物件的屬性名稱。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
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
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszQualifierName`  
[in]有效的指標`LPCWSTR`運作的限定詞名稱指定為篩選的一部分。 如需詳細資訊，請參閱 <<c0> [ 備註](#remarks)一節。 這個參數可以是 `null`。 

`lFlags`  
[in]位元欄位的組合。 如需詳細資訊，請參閱 <<c0> [ 備註](#remarks)一節。

`pQualifierValue`   
[in]有效的指標`VARIANT`結構初始化為一個篩選值。 這個參數可以是 `null`。 

`pstrNames`  
[out]A`SAFEARRAY`結構，其中包含屬性名稱。 項目，這個參數必須永遠是一個指向`null`。 請參閱[備註](#remarks)節的詳細資訊。 

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數都不是有效的或指定的旗標和參數的正確組合。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法。

傳回的具名是由控制旗標和參數的組合。 比方說，此函數可以傳回所有屬性的名稱或索引鍵屬性的名稱。  主要的篩選條件中指定`lFlags`參數和其他參數根據它而有所不同。

中的旗標值`lFlags`是位元欄位


可以做為傳遞的旗標`lEnumFlags`引數是中所定義的位元欄位*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。  您可以結合任何其他群組的任何旗標的每個群組中的一個旗標。 不過，從相同的群組的旗標是互斥的。 

| 群組 1 旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | 傳回所有屬性名稱。 `strQualifierName` 和`pQualifierVal`未使用。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 傳回具有所指定之名稱的限定詞的唯一屬性`strQualifierName`參數。 如果會使用這個旗標，您必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  傳回唯一的屬性所指定之名稱的限定詞沒有`strQualifierName`參數。 如果會使用這個旗標，您必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | 傳回具有所指定之名稱的限定詞的屬性`wszQualifierName`參數也會有等於指定的值和`pQualifierVal`結構。 如果使用這個旗標，則您必須同時指定`wszQualifierName`和`pQualifierValue`。 |

| 群組 2 旗標 |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 傳回只定義索引鍵的屬性名稱。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 傳回唯一的屬性名稱是物件參考。 |

| 群組 3 旗標 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 傳回屬於最具衍生性的類別屬性名稱。 排除的父類別中的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 傳回屬於父類別屬性名稱。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 傳回系統屬性的名稱。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 傳回非系統屬性的名稱。 |

此函式一律會配置新`SAFEARRAY`如果它傳回`WBEM_S_NO_ERROR`，和`pstrNames`一定會設定為指向它。 如果沒有屬性符合指定的篩選條件，傳回的陣列可以有 0 的項目。 如果函數傳回的值以外`WBM_S_NO_ERROR`，新`SAFEARRAY`結構並不會傳回。
 
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
