---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130377"
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
在定義 `inlineeMethodId`之模組的識別碼。 如需詳細資訊，請參閱＜備註＞一節。

`inlineeMethodId`\
在內嵌方法的識別碼。 如需詳細資訊，請參閱＜備註＞一節。

`incompleteData`\
脫銷表示 `ppEnum` 是否包含內嵌指定方法之所有方法的旗標。  如需詳細資訊，請參閱＜備註＞一節。

`ppEnum`\
脫銷列舉值的位址指標

## <a name="remarks"></a>備註

`inlineeModuleId` 和 `inlineeMethodId` 一起構成可能內嵌之方法的完整識別碼。 例如，假設模組 `A` 定義 `Simple.Add`的方法：

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

和模組 B 定義了 `Fancy.AddTwice`：

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

讓我們也假設 `Fancy.AddTwice` 內嵌呼叫 `SimpleAdd`。 分析工具可以使用這個列舉值來尋找模組 B 中定義的所有方法（內嵌 `Simple.Add`），而結果會列舉 `AddTwice`。  `inlineeModuleId` 是模組 `A`的識別碼，而 `inlineeMethodId` 是 `Simple.Add(int a, int b)`的識別碼。

如果 `incompleteData` 在函式傳回之後為 true，則列舉值不會包含內嵌指定方法的所有方法。 當 inliners 模組的一或多個直接或間接相依性尚未載入時，就會發生這種情況。 如果分析工具需要精確的資料，當載入更多模組時，最好是在每個模組載入時重試。

`EnumNgenModuleMethodsInliningThisMethod` 方法可用於解決 ReJIT 內嵌的限制。 ReJIT 可讓分析工具變更方法的執行，然後立即為其建立新程式碼。 例如，我們可以變更 `Simple.Add`，如下所示：

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

不過，因為 `Fancy.AddTwice` 已經內嵌 `Simple.Add`，所以它會繼續具有與之前相同的行為。 若要解決這項限制，呼叫者必須在內嵌 `Simple.Add` 的所有模組中搜尋所有方法，並在每個方法上使用 `ICorProfilerInfo5::RequestRejit`。 重新編譯方法時，它們會有 `Simple.Add` 的新行為，而不是舊的行為。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo6 介面](icorprofilerinfo6-interface.md)
