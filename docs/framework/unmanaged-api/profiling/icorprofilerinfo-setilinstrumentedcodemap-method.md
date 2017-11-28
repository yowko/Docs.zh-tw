---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 35c87b98a8e0c02ab6f4bca7a4f7a16ff6839c6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap 方法
設定使用指定的 Microsoft intermediate language (MSIL) 對應項目指定的函式的程式碼對應。  
  
> [!NOTE]
>  在.NET Framework 2.0 版中，呼叫`SetILInstrumentedCodeMap`上`FunctionID`代表特定應用程式網域中的泛型函式會影響該函式應用程式定義域中的所有執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]若要設定程式碼對應的函式的識別碼。  
  
 `fStartJit`  
 [in]布林值，指出是否在呼叫`SetILInstrumentedCodeMap`方法是針對特定的第一個`FunctionID`。 設定`fStartJit`至`true`中的第一個呼叫`SetILInstrumentedCodeMap`針對給定`FunctionID`，以及`false`之後。  
  
 `cILMapEntries`  
 [in]中的項目數`cILMapEntries`陣列。  
  
 `rgILMapEntries`  
 [in]COR_IL_MAP 結構陣列，其中每個指定的 MSIL 位移。  
  
## <a name="remarks"></a>備註  
 分析工具通常會以檢測方法 （例如，當到達指定的原始程式行時，通知） 插入陳述式的原始程式碼內的方法。 `SetILInstrumentedCodeMap`可讓分析工具將原始的 MSIL 指示對應至其新位置。 分析工具可以使用[icorprofilerinfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)方法來取得原始的 MSIL 位移指定的原生位移。  
  
 偵錯工具會假設每個舊的位移，是指原始、 未修改的 MSIL 程式碼中的 MSIL 位移，並且每個新的位移，是指在新的已檢測的程式碼的 MSIL 位移。 此對應應該是以遞增順序排序。 逐步執行才能正常運作，請遵循這些指導方針：  
  
-   無法重新排列已經過檢測的 MSIL 程式碼。  
  
-   請勿移除原始的 MSIL 程式碼。  
  
-   包含對應中的程式資料庫 (PDB) 檔案中的所有序列點的項目。 對應不會不進行插補遺漏的項目。 因此，根據下列對應：  
  
     (0 舊，-0 新)  
  
     (5 舊，10 新)  
  
     (9 舊，-20 新)  
  
    -   0、 1、 2、 3 或 4 的舊位移會對應至新的位移 0。  
  
    -   5、 6、 7 或 8 的舊位移會對應至新的位移 10。  
  
    -   9 或更高版本的舊位移會對應至新的位移 20。  
  
    -   0、 1、 2、 3、 4、 5、 6、 7、 8 或 9 的新位移會對應至舊的位移 0。  
  
    -   為新的位移 10、 11、 12、 13、 14、 15、 16、 17、 18 或 19 的會對應至舊的位移 5。  
  
    -   20 或更高版本的新位移會對應至舊的位移 9。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
