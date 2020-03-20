---
title: 生成派生類函數（非託管 API 引用）
description: Spawn 派生類函數創建一個從物件派生的新物件。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174845"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass 函式
從指定的物件建立新的衍生類別物件。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lFlags`  
[in] 保留。 此參數必須為 0。

`ppNewClass`  
[出]接收指向新類定義物件的指標。 如果發生錯誤，則不會返回新物件，並且`ppNewClass`未修改。 其值不能為`null`。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 出現了一個普遍的失敗。 |
| `WBEM_E_INVALID_OPERATION` | 0 x80041016 | 請求無效操作，例如從實例生成類。 |
| `WBEM_E_INCOMPLETE_CLASS` | 源類未完全定義或註冊到 Windows 管理，因此不允許使用新的派生類。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IWbem ClassObject：：spawn派生類](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法。

`ptr`必須是成為生成物件的父類的類定義。 返回的物件將成為當前物件的子類。

返回`ppNewClass`的新物件將自動成為當前物件的子類。 無法重寫此行為。 沒有其他方法可以創建子類（派生類）。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
