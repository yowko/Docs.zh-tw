---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ae413ae8944757fc90bcde752b9a5fe53cc68f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948521"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法

傳回列舉值，指定的 NGen 模組和內嵌指定的方法中所定義的所有方法。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>參數

`inlinersModuleId`\
[in]NGen 模組的識別碼。

`inlineeModuleId`\
[in]模組中定義的識別項`inlineeMethodId`。 如需詳細資訊，請參閱＜備註＞一節。

`inlineeMethodId`\
[in]內嵌方法的識別項。 如需詳細資訊，請參閱＜備註＞一節。

`incompleteData`\
[out]旗標，指出是否`ppEnum`包含內嵌的所有方法指定的方法。  如需詳細資訊，請參閱＜備註＞一節。

`ppEnum`\
[out]列舉值的位址指標

## <a name="remarks"></a>備註

`inlineeModuleId` 和`inlineeMethodId`構成可能內嵌方法的完整識別碼。 例如，假設模組`A`定義的方法`Simple.Add`:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

定義模組 B `Fancy.AddTwice`:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

我們也假設所`Fancy.AddTwice`內嵌呼叫至`SimpleAdd`。 分析工具可以使用這個列舉值，來尋找模組 B 中定義的所有方法的內嵌`Simple.Add`，並會在列舉結果`AddTwice`。  `inlineeModuleId` 是模組的識別項`A`，並`inlineeMethodId`是識別碼`Simple.Add(int a, int b)`。

如果`incompleteData`成立的函式之後傳回列舉值不包含內嵌的所有方法指定的方法。 這種情形時，或您尚未尚未載入 inliners 模組的更直接或間接的相依性。 如果程式碼剖析工具需要正確資料時，它應該稍後重試多個模組載入時，最好是在每個模組載入。

`EnumNgenModuleMethodsInliningThisMethod`方法可用來解決限制上內嵌的 ReJIT。 ReJIT 可讓您變更方法的實作，然後在即時的建立新的程式碼分析工具。 比方說，我們無法變更`Simple.Add`，如下所示：

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

不過由於`Fancy.AddTwice`具有已內嵌`Simple.Add`，它會繼續如往常有相同的行為。 若要解決這項限制，呼叫端具有所有方法的所有模組中內嵌的搜尋`Simple.Add`並用`ICorProfilerInfo5::RequestRejit`上每個這些方法。 重新編譯方法時，它們會有的新行為`Simple.Add`而不是舊的行為。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl, CorProf.h

**LIBRARY:** CorGuids.lib

**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo6 介面](icorprofilerinfo6-interface.md)