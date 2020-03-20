---
title: 克隆EnumWbem類物件函數（非託管 API 引用）
description: CloneEnumWbemClassObject 函數創建枚舉器的邏輯副本。
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175014"
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
[出]接收指向新[IEnumWbem ClassObject 的指標](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)。

`authLevel`\
[在]授權級別。

`impLevel`\
[在]類比級別。

`pCurrentEnumWbemClassObject`\
[出]指向要克隆的[IEnumWbemClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。

`strUser`\
[在]使用者名。 有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strPassword`\
[在]密碼。 有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strAuthority`\
[在]使用者的功能變數名稱。 有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 出現了一個普遍的失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可用於完成操作。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0 x80041015 | 當前進程和 WMI 之間的遠端程序呼叫 （RPC） 鏈路已失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數包裝對[IEnumWbem ClassObject：：clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法的調用。

此方法僅進行"盡力"複製。 由於許多 CIM 物件的動態性質，新的枚舉器可能不會枚舉與源枚舉器相同的物件集。

如果函式呼叫失敗，您可以通過調用[GetErrorInfo](geterrorinfo.md)函數獲取其他錯誤資訊。

## <a name="example"></a>範例

例如，請參閱[IEnumWbem 類物件：：克隆](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。

## <a name="requirements"></a>需求
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標題：** WMINet_Utils.idl

 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
