---
title: PutInstanceWmi 函式 （Unmanaged API 參考）
description: PutInstanceWmi 函式會建立或更新現有類別的執行個體。
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397509"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 函式
建立或更新現有的類別的執行個體。 執行個體寫入 WMI 存放庫。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>參數

`pInst`    
[in]要寫入的執行個體的指標。

`lFlags`   
[in]旗標的組合會影響此函式的行為。 下列的值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼： 

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，WMI 不會儲存與任何限定詞**Amended**類別。 </br> 如果未設定，系統會假設此物件不會進行當地語系化，，而且所有的限定詞是 storedwith 這個執行個體。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 如果不存在，或是如果它已經存在，覆寫它，請建立執行個體。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | 更新執行個體。 執行個體必須存在，呼叫才會成功。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | 建立執行個體。 如果執行個體已經存在，則呼叫會失敗。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會導致半同步呼叫。 |

`pCtx`  
[in]一般而言，這個值是`null`。 否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可用的提供者所提供的要求的類別的執行個體。 

`ppCallResult`  
[out]如果`null`，不使用這個參數。 如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，此函式會立即傳回並`WBEM_S_NO_ERROR`。 `ppCallResult`參數會接收到新的指標[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)物件。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有權限來更新指定類別的執行個體。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 收到 0x80041010 | 支援這個執行個體的類別不是有效的。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null`指定的屬性，不能`null`，例如標記**Indexed**或**Not_Null**限定詞。 |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定的執行個體不是有效的。 (例如，呼叫`PutInstanceWmi`類別會傳回此值。) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`指定旗標，但是執行個體已經存在。 |
| `WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` 中指定了`lFlags`，但執行個體不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)方法。

`PutInstanceWmi`函數支援建立執行個體和更新現有的類別的執行個體。  依據`pCtx`參數時，部分或所有執行個體的屬性會更新。 

當執行個體所指的`pInst`所屬的子類別化中，而 Windows 管理呼叫的所有提供者負責從子類別衍生的類別。 所有這些提供者必須能夠順利執行原始`PutInstanceWmi`要求成功。 支援的最上層的類別階層架構中的提供者會先呼叫。 呼叫順序會繼續進行的最上層類別的子類別，以及直到 Windows 管理的提供者擁有所指向的執行個體的類別，從頂端繼續往下`pInst`。
Windows Management 不會呼叫提供者來進行的任何子類別的執行個體。 

當應用程式必須更新所屬的類別階層架構中，執行個體`pInst`參數必須指向包含要修改之屬性的執行個體。 也就是考慮 目標執行個體所屬**ClassB**。 **ClassB**執行個體衍生自**ClassA**，並**ClassA**定義屬性**PropA**。 如果應用程式想要變更的值**PropA**中**ClassB**執行個體，它必須設定`pInst`該執行個體，而不是執行個體**ClassA**.

呼叫`PutInstanceWmi`抽象類別的執行個體上不在允許。

如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
