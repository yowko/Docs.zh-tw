---
title: AssemblyAttributesGoHere 類別（CompilerServices）
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: 99d7d2bbbb0586db34b5cb7a785b0448a20ab5bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446648"
---
# <a name="assemblyattributesgohere-class"></a>AssemblyAttributesGoHere 類別

供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。

## <a name="syntax"></a>語法

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a>備註

這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。 從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。 因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。

這個類型的參考會指出與安全性無關且不是多用途的自訂屬性。

這些類型在 .NET Framework 內標記為「內部」，而且位於 <xref:System.Runtime.CompilerServices> 命名空間中。

## <a name="requirements"></a>需求

mscorlib.dll

## <a name="see-also"></a>另請參閱

- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
