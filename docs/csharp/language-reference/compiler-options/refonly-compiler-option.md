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
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773858"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# 編譯器選項)

**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。 `-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。 此選項會對應到 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。

## <a name="syntax"></a>語法

```console
-refonly
```

## <a name="remarks"></a>備註

參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。 其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。 如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。

`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。

## <a name="see-also"></a>請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
