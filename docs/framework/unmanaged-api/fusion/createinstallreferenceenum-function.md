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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d696326ff8861ed8496474f76e9eaf89b4ead3e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795399"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum 函式
取得[IInstallReferenceEnum](iinstallreferenceenum-interface.md)實例的指標，表示應用程式對指定元件的參考清單。  
  
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
 脫銷傳回`IInstallReferenceEnum`的指標。  
  
 `pName`  
 在識別要列舉參考之元件的[IAssemblyName](iassemblyname-interface.md) 。  
  
 `dwFlags`  
 在會影響列舉值行為的旗標。  
  
 `pvReserved`  
 在保留以供未來擴充性之用。 `pvReserved`必須是 null 參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 融合 .dll 和 Mscorwks.dll。 請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IInstallReferenceEnum 介面](iinstallreferenceenum-interface.md)
- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
