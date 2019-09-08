---
title: CloneEnumWbemClassObject 函式（非受控 API 參考）
description: CloneEnumWbemClassObject 函數會建立枚舉器的邏輯複本。
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605314f94fd82d2a2cd7be105dde9e273f607bc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798692"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject 函式
建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a>參數

`ppEnum`\
脫銷接收新[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。

`authLevel`\
在授權層級。

`impLevel`\
在模擬層級。

`pCurrentEnumWbemClassObject`\
脫銷要複製之[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)實例的指標。

`strUser`\
在使用者名稱。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strPassword`\
在密碼。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strAuthority`\ [in] 使用者的功能變數名稱。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法的呼叫。

這個方法只會進行「最大的工作」複製。 由於許多 CIM 物件的動態本質，新的列舉值可能不會列舉與來源列舉值相同的物件集合。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="example"></a>範例

如需範例，請參閱[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。

## <a name="requirements"></a>需求
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils.idl

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
