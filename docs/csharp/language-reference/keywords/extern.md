---
title: extern 修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: d860f1a3c6917238a529093672dc5f2abc5ae066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620187"
---
# <a name="extern-c-reference"></a>extern (C# 參考)

`extern` 修飾詞是用來宣告於外部實作的方法。 `extern` 修飾詞的常見用法，是在使用 Interop 服務進行 Unmanaged 程式碼呼叫時，搭配 `DllImport` 屬性使用。 在此情況下，此方法也必須宣告為 `static`，如下列範例所示：

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` 關鍵字也可以定義外部組件別名，這樣就能從單一組件中參考相同元件的不同版本。 如需詳細資訊，請參閱[外部別名](extern-alias.md)。

同時使用 [abstract](abstract.md) 和 `extern` 修飾詞修改同一個成員是錯誤的用法。 使用 `extern` 修飾詞表示方法是在 C# 程式碼外部實作，而使用 `abstract` 修飾詞則表示類別中並未提供該方法實作。

extern 關鍵字在 C# 中的使用方式比在 C++ 中受到更多限制。 若要比較 C# 關鍵字與 C++ 關鍵字，請參閱＜使用 extern 在 C++ 語言參考中指定連結＞。

## <a name="example-1"></a>範例 1

在此範例中，程式會接收來自使用者的字串並且在訊息方塊內顯示該字串。 程式會使用從 User32.dll 程式庫匯入的 `MessageBox` 方法。

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>範例 2

此範例將示範呼叫 C 程式庫 (原生 DLL) 的 C# 程式。

1. 請建立下列 C 檔案並將它命名為 `cmdll.c`：

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. 從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並在命令提示字元中鍵入 **cl -LD cmdll.c** 來編譯 `cmdll.c` 檔案。

3. 在相同的目錄中，建立下列 C# 檔案並將它命名為 `cm.cs`：

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. 從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並輸入下列內容來編譯 `cm.cs` 檔案：

> **csc cm.cs** (適用於 x64 命令提示字元) - 或 - **csc -platform:x86 cm.cs** (適用於 x32 命令提示字元)

這樣將會建立可執行檔 `cm.exe`。

5. 執行 `cm.exe`。 `SampleMethod` 方法會將值 5 傳遞至 DLL 檔案，並傳回乘以 10 的值。  此程式會產生下列輸出：

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](modifiers.md)
