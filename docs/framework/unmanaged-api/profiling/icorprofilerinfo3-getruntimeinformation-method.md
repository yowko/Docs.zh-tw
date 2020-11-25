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
ms.openlocfilehash: fdb2b1601e0164de19bcc1e8f60856346aeaacb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698009"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation 方法

提供所分析之 common language runtime (CLR) 的版本資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 擴展進程中執行中 CLR 實例的代表性識別碼。 這與 `ClrInstanceID` Windows 事件追蹤 (ETW) 啟動事件報表相同。  
  
 `pRuntimeType`  
 擴展執行時間型別。 此參數會 `COR_PRF_DESKTOP_CLR` 針對適用于 clr 的桌上出版本，或用於 `COR_PRF_CORE_CLR` Silverlight 中所使用之 clr 的核心版本傳回。  
  
 `pMajorVersion`  
 擴展CLR 的主要版本號碼。  
  
 `pMinorVersion`  
 擴展CLR 的次要版本號碼。  
  
 `pBuildVersion`  
 擴展CLR 的組建版本號碼。  
  
 `pQFEVersion`  
 擴展與軟體更新相關聯之 CLR 的版本號碼。  
  
 `cchVersionString`  
 在指向之緩衝區的長度（以字元為單位） `szVersionString` 。  
  
 `pcchVersionString`  
 擴展的長度（以字元為單位） `szVersionString` 。  
  
 `szVersionString`  
 擴展CLR 版本字串。  
  
## <a name="remarks"></a>備註  

 您可以針對任何參數傳遞 null。 不過， `pcchVersionString` 除非也是 null，否則不可以是 null `szVersionString` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
