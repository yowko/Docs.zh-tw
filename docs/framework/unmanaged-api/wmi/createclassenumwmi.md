---
title: CreateClassEnumWmi 函式 （Unmanaged API 參考）
description: CreateClassEnumWmi 函式會傳回符合指定的條件的所有類別的列舉值。
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a4d2c2bd28640d0ac7124f8e0864e9e72fb1eb9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372330"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi 函式
傳回滿足所指定選取條件之所有類別的列舉程式。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>參數

`strSuperclass`\
[in]如果沒有`null`或空的時，指定的父類別; 名稱的列舉值會傳回這個類別的子類別。 如果它是`null`或空白和`lFlags`WBEM_FLAG_SHALLOW，傳回最上層類別 （沒有父類別的類別）。 如果它是`null`或空白並`lFlags`是`WBEM_FLAG_DEEP`，傳回命名空間中的所有類別。

`lFlags`\
[in]旗標的組合會影響此函式的行為。 下列的值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果集、 函式會擷取已修改儲存在目前連接的地區設定當地語系化的命名空間中的限定詞。 <br/> 如果沒有設定，此函數會擷取立即的命名空間中儲存的辨識符號。 |
| `WBEM_FLAG_DEEP` | 0 | 列舉型別在階層中，但不是此類別包含所有子類別。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列舉型別包含這個類別只單純執行個體，並排除所有執行個體，提供這個類別中找不到屬性的子類別。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會導致半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向的列舉值。 一般而言，順向的列舉值會比較快，並使用較少的記憶體，比傳統的列舉值，但不是允許呼叫[複製品](clone.md)。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | 之前在發行時，WMI 就會保留在列舉中的物件的指標。 |

建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。

`pCtx`\
[in]一般而言，這個值是`null`。 否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可用的提供者所提供的要求的類別的執行個體。

`ppEnum`\
[out]接收列舉值的指標。

`authLevel`\
[in]授權層級。

`impLevel`\
[in]模擬等級。

`pCurrentNamespace`\
[in]指標[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件，表示目前的命名空間。

`strUser`\
[in]使用者名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strPassword`\
[in]密碼。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strAuthority`\
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有檢視一個或多個函式會傳回類別的權限。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` 不存在。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[iwbemservices:: Createclassenum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum)方法。

如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)