---
title: -refout (C# 編譯器選項)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771765"
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

引用程式集是一種特殊類型的程式集，僅包含表示庫的公共 API 曲面所需的最小中繼資料量。 它們包括在生成工具中引用程式集時具有重大意義的所有成員的聲明，但不包括對其 API 協定沒有可觀察到影響的所有成員的實現和聲明。 有關詳細資訊，請參閱 .NET 指南中的[參考程式集](../../../standard/assembly/reference-assemblies.md)。

`-refout`和[`-refonly`](refonly-compiler-option.md)選項是互斥的。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
