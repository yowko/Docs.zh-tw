---
title: CreateInstallReferenceEnum 函式
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: 0f62b05ebbd8b27dba160c8281c1d40748c90fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688831"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum 函式

取得 [IInstallReferenceEnum](iinstallreferenceenum-interface.md) 實例的指標，該實例表示應用程式對指定元件的參考清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>參數  

 `ppRefEnum`  
 擴展傳回的 `IInstallReferenceEnum` 指標。  
  
 `pName`  
 在識別要列舉參考之元件的 [IAssemblyName](iassemblyname-interface.md) 。  
  
 `dwFlags`  
 在影響列舉值行為的旗標。  
  
 `pvReserved`  
 在保留供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** Fusion.dll 和 Mscorwks.dll。 使用 Fusion.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IInstallReferenceEnum 介面](iinstallreferenceenum-interface.md)
- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
