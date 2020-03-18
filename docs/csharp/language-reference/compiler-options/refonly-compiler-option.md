---
title: -refonly (C# 編譯器選項)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773858"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# 編譯器選項)

**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。 `-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。 此選項會對應到 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。

## <a name="syntax"></a>語法

```console
-refonly
```

## <a name="remarks"></a>備註

引用程式集是一種特殊類型的程式集，僅包含表示庫的公共 API 曲面所需的最小中繼資料量。 它們包括在生成工具中引用程式集時具有重大意義的所有成員的聲明，但不包括對其 API 協定沒有可觀察到影響的所有成員的實現和聲明。 有關詳細資訊，請參閱 .NET 指南中的[參考程式集](../../../standard/assembly/reference-assemblies.md)。

`-refonly`和[`-refout`](refout-compiler-option.md)選項是互斥的。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
