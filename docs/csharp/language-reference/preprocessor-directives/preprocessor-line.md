---
title: '#line - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608533"
---
# <a name="line-c-reference"></a>#line (C# 參考)

`#line` 可讓您修改編譯器的行號以及 (選擇性) 錯誤和警告的檔案名稱輸出。

下列範例示範如何報告兩個與行號建立關聯的警告。 `#line 200` 指示詞會將下一行的行號強制為 200 (但預設值為 #6)，而且在下一個 `#line` 指示詞之前，檔案名稱將會回報為 "Special"。 `#line default` 指示詞會將行編號還原為其預設編號，這會計算已由先前的指示詞重新編號的行。

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

編譯會產生下列輸出：

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>備註

`#line` 指示詞可以用於建置程序中的自動化中繼步驟。 例如，如果已從原始程式碼檔中移除行，但您仍然想要編譯器根據檔案中的原始行編號來產生輸出，則可以移除行，然後模擬具有 `#line` 的原始行編號。

`#line hidden` 指示詞會隱藏偵錯工具中的後續行，如此一來，開發人員逐步執行程式碼時，會逐步執行 `#line hidden` 與下一個 `#line` 指示詞 (假設它不是另一個 `#line hidden` 指示詞) 之間的任何行。 此選項也可用來讓 ASP.NET 區分使用者定義的程式碼與電腦產生的程式碼。 雖然 ASP.NET 是這項功能的主要取用者，但是可能會有更多來源產生器利用它。

`#line hidden` 指示詞不會影響錯誤報告中的檔案名稱或行號。 也就是說，如果隱藏區塊中發生錯誤，則編譯器會報告錯誤的目前檔案名稱和行號。

`#line filename` 指示詞指定您想要在編譯器輸出中顯示的檔案名稱。 預設會使用原始程式碼檔的實際名稱。 檔案名稱必須以雙引號 ("") 括住，而且前面必須有行號。

原始程式碼檔可以有任意數目的 `#line` 指示詞。

## <a name="example-1"></a>範例 1

下列範例示範偵錯工具如何忽略程式碼中的隱藏行。 當您執行範例時，會顯示三行文字。 不過，如果您設定中斷點 (如此範例所示)，並按 F10 逐步執行程式碼，則會注意到偵錯工具忽略隱藏行。 另請注意，即使您在隱藏行設定中斷點，偵錯工具仍然會忽略它。

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](./index.md)
