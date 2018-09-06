---
title: CloneEnumWbemClassObject 函式 （Unmanaged API 參考）
description: CloneEnumWbemClassObject 函式可讓列舉值的邏輯複本。
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
ms.openlocfilehash: 35bd458eb6046f57d37764e0a8e58616f2c2c3a1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778528"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject 函式
建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
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

`ppEnum`  
[out]接收新指標[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)。

`authLevel`  
[in]授權層級。

`impLevel` [in]模擬等級。

`pCurrentEnumWbemClassObject`  
[out]指標[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)要複製的執行個體。

`strUser`   
[in]使用者名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strPassword`   
[in]密碼。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strAuthority`   
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。

這個方法會建立僅 「 盡力 」 的複本。 由於許多 CIM 物件的動態本質，就可以將新的列舉值不會列舉的物件與來源列舉值相同的組。  

如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="example"></a>範例

如需範例，請參閱[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
