---
title: "IMetaDataConverter::GetTypeLibFromMetaData 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetTypeLibFromMetaData
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b2b12c5f3ecb0d30fad3bfb5c96e0e66fd9ee7bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>IMetaDataConverter::GetTypeLibFromMetaData 方法
取得指標`ITypeLib`代表有指定的程式庫和模組名稱的類型程式庫的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a>參數  
 `strModule`  
 [in]類型程式庫模組的名稱。  
  
 `strTlbName`  
 [in]類型程式庫的名稱。  
  
 `ppITL`  
 [out]接收的位址的位置的指標`ITypeLib`執行個體，表示型別程式庫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataConverter 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
