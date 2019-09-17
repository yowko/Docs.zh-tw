---
title: PutInstanceWmi 函式（非受控 API 參考）
description: PutInstanceWmi 函數會建立或更新現有類別的實例。
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
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798367"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 函式

建立或更新現有類別的執行個體。 執行個體是寫入到 WMI 存放庫。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>參數

`pInst`\
在要寫入之實例的指標。

`lFlags`\
在會影響此函式行為的旗標組合。 下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，WMI 不會將任何限定詞儲存為**修改**過的類別。 <br> 如果未設定，則會假設此物件未當地語系化，而且所有限定詞都會與這個實例一起儲存。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 如果實例不存在，請建立它，如果它已經存在，則予以覆寫。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | 更新實例。 實例必須存在，呼叫才會成功。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | 建立實例。 如果實例已經存在，呼叫就會失敗。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |

`pCtx`\
在通常，此值為`null`。 否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。

`ppCallResult`\
脫銷如果`null`為，則不會使用這個參數。 如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY` ，`WBEM_S_NO_ERROR`則函式會立即傳回。 `ppCallResult` 參數會接收新 [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) 物件的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有許可權可更新指定之類別的實例。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 支援這個實例的類別無效。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | 針對不能為`null`的屬性指定，例如由**索引**或 Not_Null 限定詞標記的。 `null` |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定的實例無效。 （例如，使用類別`PutInstanceWmi`呼叫會傳回這個值）。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | 已`WBEM_FLAG_CREATE_ONLY`指定旗標，但實例已經存在。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`已在中`lFlags`指定，但實例不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫[ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemServices：:P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)方法的呼叫。

`PutInstanceWmi`函數只支援建立實例，以及更新現有類別的實例。  視`pCtx`參數的設定方式而定，會更新實例的部分或所有屬性。

當所指`pInst`的實例屬於子類別時，Windows 管理會呼叫所有負責子類別衍生來源的提供者。 所有這些提供者都必須成功，原始`PutInstanceWmi`要求才會成功。 首先會呼叫支援階層中最上層類別的提供者。 呼叫順序會繼續使用最上層類別的子類別，並從上到下繼續進行，直到 Windows 管理到達擁有所指向`pInst`之實例的類別提供者為止。
Windows 管理不會呼叫實例之任何子類別的提供者。

當應用程式必須更新屬於類別階層的實例時， `pInst`參數必須指向包含要修改之屬性的實例。 也就是，請考慮屬於**ClassB**的目標實例。 **ClassB**實例衍生自**ClassA**，而**ClassA**定義屬性**PropA**。 如果應用程式想要變更**ClassB**實例中的`pInst` **PropA**值，它必須將設定為該實例，而不是**ClassA**的實例。

不`PutInstanceWmi`允許在抽象類別的實例上呼叫。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
