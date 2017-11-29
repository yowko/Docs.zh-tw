---
title: "IManagedObject::GetObjectIdentity 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c0dabfca147b203c3bcf93a362e6670ae295338
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity 方法
取得此受管理物件識別。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pBSTRGUID`  
 [out]物件所在的程序的 GUID 指標。  
  
 `AppDomainID`  
 [out]物件的應用程式定義域的識別碼指標。  
  
 `pCCW`  
 [out]物件的索引，在 COM 傳統 v-table 指標。  
  
## <a name="remarks"></a>備註  
 受管理物件的識別則包括 COM 傳統 v-table 中處理程序的 GUID、 應用程式網域識別碼，以及物件的索引。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IManagedObject 介面](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
