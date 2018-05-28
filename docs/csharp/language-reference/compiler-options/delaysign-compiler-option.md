---
title: -delaysign (C# 編譯器選項)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# 編譯器選項)

這個選項可讓編譯器保留輸出檔案中的空間，以便稍後新增數位簽章。

## <a name="syntax"></a>語法

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>引數

`+` &#124; `-`

如果需要完整簽署的組件，請使用 **-delaysign-**。 如果只想在組件中放置公開金鑰，請使用 **-delaysign+**。 預設值為 **-delaysign-**。

## <a name="remarks"></a>備註

**-delaysign** 選項必須搭配 [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 或 [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) 才有作用。

**-delaysign** 和 **-publicsign** 選項是互斥的。

當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。 該作業會建立數位簽章，並儲存於包含資訊清單的檔案中。 當延遲簽署組件時，編譯器不會去計算和儲存簽章，但會保留檔案中的空間，以便稍後再加入簽章。

例如，使用 **-delaysign+** 時，可讓測試人員將組件放入全域快取中。 測試之後，您可以使用 [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) 公用程式將私密金鑰放入組件中，以完整簽署組件。

如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性]  頁面。
1. 修改 [僅延遲簽署] 屬性。

如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。

## <a name="see-also"></a>請參閱

 [C# -publicsign 選項](publicsign-compiler-option.md)  
 [C# 編譯器選項](index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
