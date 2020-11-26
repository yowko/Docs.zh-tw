---
description: -refonly (C# 編譯器選項)
title: -refonly (C# 編譯器選項)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "89124743"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# 編譯器選項)

**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。 `-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。 此選項會對應到 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。

## <a name="syntax"></a>語法

```console
-refonly
```

## <a name="remarks"></a>備註

參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最少量中繼資料。 它們包括在組建工具中參考元件時，所有重要成員的宣告，但排除對其 API 合約沒有任何影響的私用成員的所有成員執行和宣告。 如需詳細資訊，請參閱 .NET 指南中的 [參考元件](../../../standard/assembly/reference-assemblies.md) 。

`-refonly`和 [`-refout`](refout-compiler-option.md) 選項都是互斥的。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
