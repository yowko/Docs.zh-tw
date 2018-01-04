---
title: "IAssemblyCacheItem::CreateStream 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem.CreateStream
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a24d9732a8e413b3cde0ac1c622743153ff6fd01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream 方法
建立具有指定的名稱和格式的資料流。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFlags`  
 [in]支援下列值： 旗標。  
  
 `pszStreamName`  
 [in]要建立之資料流名稱。  
  
 `dwFormat`  
 [in]要進行資料流處理的檔案格式。  
  
 `dwFormatFlags`  
 [in]支援下列值： 格式特有的旗標。  
  
 `ppIStream`  
 [out]傳回的位址指標<xref:IStream>執行個體。  
  
 `puliMaxSize`  
 [in，選用]所參考的資料流的大小上限`ppIStream`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IAssemblyCacheItem 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
