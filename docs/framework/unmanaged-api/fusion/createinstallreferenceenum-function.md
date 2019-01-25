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
ms.openlocfilehash: 5ec212bd999fe32e56a272c9bc3f39e19617a250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547760"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum 函式
取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示指定的組件的應用程式的參考清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `ppRefEnum`  
 [out]傳回`IInstallReferenceEnum`指標。  
  
 `pName`  
 [in][IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)識別要列舉的參考組件。  
  
 `dwFlags`  
 [in]影響列舉值的行為的旗標。  
  
 `pvReserved`  
 [in]保留供未來擴充。 `pvReserved` 必須是 null 參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：** Fusion.dll 和 Mscorwks.dll。 使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 的正確版本。  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IInstallReferenceEnum 介面](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
