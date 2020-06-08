---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495524"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法

傳回指定之 NGen 模組中所定義之所有方法的列舉值，並內嵌指定的方法。

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
在NGen 模組的識別碼。

`inlineeModuleId`\
在定義之模組的識別碼 `inlineeMethodId` 。 如需詳細資訊，請參閱「備註」一節。

`inlineeMethodId`\
在內嵌方法的識別碼。 如需詳細資訊，請參閱「備註」一節。

`incompleteData`\
脫銷表示是否 `ppEnum` 包含所有方法內嵌指定方法的旗標。  如需詳細資訊，請參閱「備註」一節。

`ppEnum`\
脫銷列舉值的位址指標

## <a name="remarks"></a>備註

`inlineeModuleId`和 `inlineeMethodId` 會構成可能內嵌之方法的完整識別碼。 例如，假設模組 `A` 定義了方法 `Simple.Add` ：

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

和模組 B 定義 `Fancy.AddTwice` ：

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

讓也假設 `Fancy.AddTwice` 內嵌呼叫 `SimpleAdd` 。 分析工具可以使用這個列舉值來尋找模組 B 中定義的所有方法（內嵌 `Simple.Add` ），而結果會列舉 `AddTwice` 。  `inlineeModuleId`是模組的識別碼 `A` ，而 `inlineeMethodId` 是的識別碼 `Simple.Add(int a, int b)` 。

如果在函式傳回 `incompleteData` 之後為 true，列舉值就不會包含內嵌指定方法的所有方法。 當 inliners 模組的一或多個直接或間接相依性尚未載入時，就會發生這種情況。 如果分析工具需要精確的資料，當載入更多模組時，最好是在每個模組載入時重試。

`EnumNgenModuleMethodsInliningThisMethod`方法可以用來解決 ReJIT 內嵌的限制。 ReJIT 可讓分析工具變更方法的執行，然後立即為其建立新程式碼。 例如，我們可以變更 `Simple.Add` 如下：

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

不過，因為已經 `Fancy.AddTwice` 內嵌 `Simple.Add` ，所以它會繼續具有與之前相同的行為。 若要解決這項限制，呼叫者必須在所有模組中搜尋所有方法，以內嵌 `Simple.Add` 和使用 `ICorProfilerInfo5::RequestRejit` 這些方法。 重新編譯方法時，會有新的行為， `Simple.Add` 而不是舊的行為。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo6 介面](icorprofilerinfo6-interface.md)
