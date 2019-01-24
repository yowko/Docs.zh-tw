---
title: QualifierSet_BeginEnumeration 函式 （Unmanaged API 參考）
description: QualifierSet_BeginEnumeration 函式會重設物件限定詞的列舉值。
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3577c90af51886868d57796fb5bfae91dedcee16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720115"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration 函式
將物件限定詞的列舉程式重設為列舉開始時的狀態。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>參數

`vFunc`   
[in]未使用此參數。

`ptr`   
[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。

`lFlags`   
[in]中所述的旗標的位元組合[備註](#remarks)區段，指定要包含在列舉中的限定詞。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` 參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`QualifierSet_BeginEnumeration`而不需要的介入呼叫進行[ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可供開始新的列舉型別。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)方法。

若要列舉所有的物件上的限定詞，必須呼叫這個方法的第一個呼叫之前[QualifierSet_Next](qualifierset-next.md)。 限定詞會列舉在其中的順序保證會針對指定的列舉型別而異。

可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。   

|常數  |值  |描述  |
|---------|---------|---------|
|  | 0 | 傳回所有限定詞的名稱。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 傳回目前的屬性或物件特定限定詞的名稱。 <br/> 屬性：傳回只特有的屬性 （包括覆寫） 限定詞，並不會傳播從類別定義的限定詞。 <br/> 執行個體：傳回只有特定執行個體的限定詞名稱。 <br/> 類別：傳回衍生的類別 beiong 特定只限定詞。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 傳回的傳播的限定詞的名稱，從另一個物件。 <br/> 屬性：傳回只限定詞傳播至這個屬性從類別定義中，而不從本身的屬性。 <br/> 執行個體：傳回的只有這些限定詞傳播，從類別定義。 <br/> 類別：傳回繼承自父類別的只有這些限定詞的名稱。 |

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱
- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
