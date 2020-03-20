---
title: PutMethod 函數（非託管 API 引用）
description: PutMethod 函數創建一個方法。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174910"
---
# <a name="putmethod-function"></a>PutMethod 函式
建立方法。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszName`  
[在]要創建的方法的名稱。

`lFlags`  
[in] 保留。 此參數必須為 0。

`pSignatureIn`  
[在]指向包含方法參數[的__Parameters系統類](/windows/desktop/WmiSdk/--parameters)`in`副本的指標。 如果設置為`null`，則忽略此參數。  

`pSignatureOut`  
[在] 指向包含方法參數[的__Parameters系統類](/windows/desktop/WmiSdk/--parameters)`out`副本的指標。 如果設置為`null`，則忽略此參數。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一個或多個參數無效。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0 x80041043 | 在`[in, out]` *pInSignature*和*pOutSignature*物件中指定的方法參數具有不同的限定詞。
| `WBEM_E_MISSING_PARAMETER_ID` | 0 x80041036 | 缺少**ID**限定詞的規範的方法參數。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0 x80041038 | 分配給方法參數的 ID 系列不是連續的，也不是從 0 開始的。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0 x80041039 | 方法的傳回值具有**ID**限定詞。 |
| `WBEM_E_PROPAGATED_METHOD` | 0 x80041034 | 嘗試從父類重用現有方法名稱，並且簽名不匹配。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbemClassObject：:PutMethod 方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)調用。

僅當是 CIM 類定義`ptr`時，才支援此方法調用。 方法操作從指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標中不可用。

使用者無法創建名稱以底線開頭或結尾的方法。 這是為系統類和屬性保留的。

對於方法，`in`和`out`參數被描述為[IWbemClassObject 物件](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)中的屬性。

`[in/out]`可以通過將相同的屬性添加到 和`pInSignature``pOutSignature`參數指向的兩個物件來定義參數。 在這種情況下，屬性共用相同的**ID**限定詞值。

[__Parameters](/windows/desktop/WmiSdk/--parameters)類物件中的每個屬性除必須具有`ReturnValue`**ID**限定詞外，該限定詞是標識參數顯示順序的零基數值。 沒有兩個參數可以具有相同的**ID**值，並且不能跳過**ID**值。 如果發生任一條件，`PutMethod`則函數`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`將返回 。

## <a name="example"></a>範例

例如，請參閱[IWbemClassObject：:PutMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
