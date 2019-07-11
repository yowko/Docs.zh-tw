---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742253"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。

## <a name="syntax"></a>語法

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>備註

這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。 從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。 因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。

這個類型的參考會指出與安全性相關且不是多用途的自訂屬性。

這些類型會標示 「 內部 」 在.NET Framework 中，位於<xref:System.Runtime.CompilerServices>命名空間。

## <a name="requirements"></a>需求

mscorlib.dll

## <a name="see-also"></a>另請參閱

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
