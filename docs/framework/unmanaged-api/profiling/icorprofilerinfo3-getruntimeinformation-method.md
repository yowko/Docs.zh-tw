---
title: "ICorProfilerInfo3::GetRuntimeInformation 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetRuntimeInformation Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a18f0604b1585ffb1dd8230c289bcd95bfa3dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation 方法
提供有關 common language runtime (CLR) 所分析的版本資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>參數  
 `pClrInstanceId`  
 [out]代表處理程序中正在執行 CLR 執行個體識別碼。 這是與相同`ClrInstanceID`Windows (ETW) 啟動事件的事件追蹤的報告。  
  
 `pRuntimeType`  
 [out]執行階段型別。 這個參數會傳回`COR_PRF_DESKTOP_CLR`桌面版本的 CLR 或`COR_PRF_CORE_CLR`核心版本的 Silverlight 中使用的 CLR。  
  
 `pMajorVersion`  
 [out]在 CLR 的主要版本號碼。  
  
 `pMinorVersion`  
 [out]在 CLR 的次要版本號碼。  
  
 `pBuildVersion`  
 [out]CLR 組建版本號碼。  
  
 `pQFEVersion`  
 [out]軟體更新相關聯的 clr 版本號碼。  
  
 `cchVersionString`  
 [in]長度，以字元為單位的緩衝區，`szVersionString`指向。  
  
 `pcchVersionString`  
 [out]長度，以字元為單位的`szVersionString`。  
  
 `szVersionString`  
 [out]CLR 版本字串。  
  
## <a name="remarks"></a>備註  
 您可以傳遞任何參數為 null。 不過，`pcchVersionString`不可為 null 除非`szVersionString`也是 null。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
