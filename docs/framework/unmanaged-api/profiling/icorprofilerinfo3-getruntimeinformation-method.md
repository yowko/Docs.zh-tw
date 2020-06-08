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
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496395"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation 方法
提供所分析之 common language runtime （CLR）的版本資訊。  
  
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
 脫銷進程中執行中 CLR 實例的代表識別碼。 這與 `ClrInstanceID` Windows 事件追蹤（ETW）啟動附隨報告的相同。  
  
 `pRuntimeType`  
 脫銷執行時間類型。 這個參數會 `COR_PRF_DESKTOP_CLR` 針對 clr 的桌上出版本或 `COR_PRF_CORE_CLR` Silverlight 中使用的 clr 核心版本傳回。  
  
 `pMajorVersion`  
 脫銷CLR 的主要版本號碼。  
  
 `pMinorVersion`  
 脫銷CLR 的次要版本號碼。  
  
 `pBuildVersion`  
 脫銷CLR 的組建版本號碼。  
  
 `pQFEVersion`  
 脫銷與軟體更新相關聯之 CLR 的版本號碼。  
  
 `cchVersionString`  
 在指向之緩衝區的長度（以字元為單位） `szVersionString` 。  
  
 `pcchVersionString`  
 脫銷的長度（以字元為單位） `szVersionString` 。  
  
 `szVersionString`  
 脫銷CLR 版本字串。  
  
## <a name="remarks"></a>備註  
 您可以為任何參數傳遞 null。 不過， `pcchVersionString` 除非也是 null，否則不可以是 null `szVersionString` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
