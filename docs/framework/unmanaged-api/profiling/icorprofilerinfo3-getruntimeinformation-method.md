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
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868547"
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
 脫銷進程中執行中 CLR 實例的代表識別碼。 這與 Windows 事件追蹤（ETW）啟動附隨報告的 `ClrInstanceID` 相同。  
  
 `pRuntimeType`  
 脫銷執行時間類型。 此參數會傳回適用于 CLR 桌上出版本的 `COR_PRF_DESKTOP_CLR`，或用於 Silverlight 中所使用之 CLR 核心版本的 `COR_PRF_CORE_CLR`。  
  
 `pMajorVersion`  
 脫銷CLR 的主要版本號碼。  
  
 `pMinorVersion`  
 脫銷CLR 的次要版本號碼。  
  
 `pBuildVersion`  
 脫銷CLR 的組建版本號碼。  
  
 `pQFEVersion`  
 脫銷與軟體更新相關聯之 CLR 的版本號碼。  
  
 `cchVersionString`  
 在`szVersionString` 指向之緩衝區的長度（以字元為單位）。  
  
 `pcchVersionString`  
 脫銷`szVersionString`的長度（以字元為單位）。  
  
 `szVersionString`  
 脫銷CLR 版本字串。  
  
## <a name="remarks"></a>備註  
 您可以為任何參數傳遞 null。 不過，除非 `szVersionString` 也是 null，否則 `pcchVersionString` 不可以是 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
