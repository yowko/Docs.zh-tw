---
title: 常見資料類型 (Unmanaged API 參考)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b0a27eae744fb22c87634aaf6a0274a9825d981
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776474"
---
# <a name="common-data-types-unmanaged-api-reference"></a>常見資料類型 (Unmanaged API 參考)
本主題針對 C/C++ `typedef` 陳述式所定義的 .NET Framework，列出 Unmanaged API 所使用的簡單資料類型。 這些資料類型通常是 C/C++ 基本資料類型的別名。 一般而言，這些資料類型的值為不透明；因此，會由特定函式或方法傳回這些值，如此一來就能在未經修改的情況下將這些值傳遞至其他函式或方法。  
  
|資料類型|定義|定義於|描述|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|應用程式網域的識別項。|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|組件的識別項。|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|Managed 類別的識別項。|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|clrdata.h|64位的記憶體位址。|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|無法使用|64位的記憶體位址。|
|CONNID|`typedef DWORD CONNID;`|cordebug.h、mscoree.h|連接至 Microsoft SQL Server 執行個體的執行緒的連接識別項。|  
|ContextID|`typedef UINT_PTR ContextID;`|corprof.h|與特定 Managed 執行緒相關之內容的識別項。|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|代表特定堆疊框架之資訊的不透明處理常式。|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|指向堆疊框架的不透明處理常式。 其只在被傳遞時的回呼期間有效。|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|記憶體中的位址。|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|接續的狀態。|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|CPU 註冊的值。|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|函式或方法的識別項。|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|記憶體回收處理常式。|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|cordebug.h|方法定義 token。|
|mdToken|`typedef UINT32 mdToken;`|corprof.h|元資料標記（中繼資料資料表中的一列）。|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|組件模組的識別項。|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|物件的識別項。|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|cordebug.h|成員或中繼資料簽章的指標。|
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|Managed 處理序的識別項。|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|JIT 編譯的函式識別項。|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|corsym。h|64位記憶體位址的指標。|
|TASKID|`typedef UINT64 TASKID;`|cordebug.h、mscoree.h|[ICLRTask](./hosting/iclrtask-interface.md)實例的識別碼。|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|Managed 執行緒的識別項。|  
  
## <a name="see-also"></a>另請參閱

- [Unmanaged API 參考](index.md)
