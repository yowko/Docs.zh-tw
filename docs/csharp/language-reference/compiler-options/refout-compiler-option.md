---
description: -refout (C# 編譯器選項)
title: -refout (C# 編譯器選項)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128710"
---
# <a name="-refout-c-compiler-options"></a>-refout (C# 編譯器選項)

**-refout** 選項指定參考組件應該輸出的檔案路徑。 這在發出 API 中會轉譯成 `metadataPeStream`。 此選項會對應到 MSBuild 的 [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。

## <a name="syntax"></a>語法

```console
-refout:filepath
```

## <a name="arguments"></a>引數

 `filepath` 參考組件的檔案路徑。 它通常應該符合主要組件的路徑。 建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。

## <a name="remarks"></a>備註

參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最少量中繼資料。 它們包括在組建工具中參考元件時，所有重要成員的宣告，但排除對其 API 合約沒有任何影響的私用成員的所有成員執行和宣告。 如需詳細資訊，請參閱 .NET 指南中的 [參考元件](../../../standard/assembly/reference-assemblies.md) 。

`-refout`和 [`-refonly`](refonly-compiler-option.md) 選項都是互斥的。

## <a name="see-also"></a>另請參閱

- [C # 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
