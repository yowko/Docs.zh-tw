---
title: ICorProfilerInfo3::GetRuntimeInformation 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164927"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation 方法
提供 common language runtime (CLR) 所分析的版本資訊。  
  
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
  
## <a name="parameters"></a>參數  
 `pClrInstanceId`  
 [out]代表處理序中執行 CLR 執行個體的識別碼。 這是與相同`ClrInstanceID`Windows (ETW) 啟動事件的事件追蹤報告。  
  
 `pRuntimeType`  
 [out]執行階段型別。 此參數會傳回`COR_PRF_DESKTOP_CLR`桌面版本的 CLR 或`COR_PRF_CORE_CLR`CLR 在 Silverlight 中使用的核心版本。  
  
 `pMajorVersion`  
 [out]CLR 的主要版本號碼。  
  
 `pMinorVersion`  
 [out]CLR 的次要版本號碼。  
  
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
 您可以傳遞任何參數為 null。 不過，`pcchVersionString`不得為 null 除非`szVersionString`也是 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
