---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400535"
---
# <a name="-optionstrict"></a>-optionstrict

強制執行嚴格的類型語義來限制隱含類型轉換。

## <a name="syntax"></a>語法

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>引數

`+` &#124; `-`  
選擇性。 `-optionstrict+`選項會限制隱含類型轉換。 此選項的預設值為 `-optionstrict-` 。 `-optionstrict+`選項與相同 `-optionstrict` 。 您可以針對寬鬆類型的語義使用這兩者。

`custom`  
必要。 不遵守嚴格語言語義時發出警告。

## <a name="remarks"></a>備註

當 `-optionstrict+` 生效時，只有擴展型別轉換可以隱含地進行。 隱含的縮小類型轉換（例如將 `Decimal` 類型物件指派給整數類型物件）會回報為錯誤。

若要產生隱含縮小類型轉換的警告，請使用 `-optionstrict:custom` 。 用 `-nowarn:numberlist` 來忽略特定的警告，並 `-warnaserror:numberlist` 將特定警告視為錯誤。

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionstrict

1. 在 **方案總管**中選取專案。 在 [**專案**] 功能表上，按一下 [**屬性]。**

2. 按一下 [編譯]**** 索引標籤。

3. 修改 [**選項 Strict** ] 方塊中的值。

### <a name="to-set--optionstrict-programmatically"></a>以程式設計方式設定-optionstrict

請參閱[Option Strict 語句](../../language-reference/statements/option-strict-statement.md)。

## <a name="example"></a>範例

下列程式碼會 `Test.vb` 使用 strict 類型的語義進行編譯。

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror （Visual Basic）](warnaserror.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Long](../../language-reference/statements/option-strict-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
