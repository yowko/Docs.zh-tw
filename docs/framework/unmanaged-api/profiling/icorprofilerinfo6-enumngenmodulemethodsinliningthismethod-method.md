---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e11dd1c24001c764c82ed3f11336873ee57b2e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
[在.NET Framework 4.6 和更新版本中支援]  
  
 提供的 NGen 模組和內嵌指定的方法中所定義的所有方法傳回的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `inlinersModuleId`  
 [in]NGen 模組的識別碼。  
  
 `inlineeModuleId`  
 [in]定義模組的識別碼`inlineeMethodId`。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `inlineeMethodId`  
 [in]內嵌的方法識別項。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `incompleteData`  
 [out]旗標，指出是否`ppEnum`包含內嵌的所有方法指定的方法。  如需詳細資訊，請參閱＜備註＞一節。  
  
 `ppEnum`  
 [out]列舉值的位址指標  
  
## <a name="remarks"></a>備註  
 `inlineeModuleId`和`inlineeMethodId`結合在一起形成完整的識別項可能是內嵌的方法。 例如，假設模組`A`定義的方法`Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 和模組 Bdefines `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 我們也假設，`Fancy.AddTwice`內嵌呼叫至`SimpleAdd`。 分析工具可以使用這個列舉值，來尋找模組 B 中定義的所有方法的內嵌`Simple.Add`，並會列舉結果`AddTwice`。  `inlineeModuleId`為模組的識別碼`A`，和`inlineeeMethodId`識別`Simple.Add(int a, int b)`。  
  
 如果`incompleteData`成立的函式之後傳回列舉值不包含內嵌的所有方法指定的方法。 這種情形時，或尚未尚未載入的模組 inliners 更直接或間接的相依性。 如果分析工具需要正確資料時，它應該稍後重試多個模組載入時，最好是在每個模組載入。  
  
 `EnumNgenModuleMethodsInliningThisMethod`方法可用來解決限制上內嵌的 ReJIT。 ReJIT 可讓您變更方法的實作，然後為其建立新的程式碼即時分析工具。 例如，我們可以變更`Simple.Add`，如下所示：  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 但是因為`Fancy.AddTwice`具有已內嵌`Simple.Add`，它會繼續如往常一般有相同的行為。 若要解決這項限制，呼叫端必須搜尋所有方法中的所有模組的內嵌`Simple.Add`並用`ICorProfilerInfo5::RequestRejit`上每個這些方法。 重新編譯方法時，他們必須的新行為`Simple.Add`而不是舊的行為。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo6 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
