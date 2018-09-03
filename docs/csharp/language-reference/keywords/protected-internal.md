---
title: protected internal (C# 參考)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 1a305cb84989f12350e2e7cc28dd18f9d0c7ae5e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43387557"
---
# <a name="protected-internal-c-reference"></a>protected internal (C# 參考)

`protected internal` 關鍵字組合是成員存取修飾詞。 protected internal 成員可以從目前的組件或衍生自包含類別的類型存取。 如需 `protected internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。

## <a name="example"></a>範例

基底類別的 protected internal 成員可以從其包含組件內的任何類型存取。 它也可以在位於另一個組件的衍生類別內存取，但只能是在透過衍生類別類型的變數進行存取之時。 例如，請考慮下列程式碼區段：

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```
此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。
第一個檔案包含公用的基底類別 `BaseClass`，以及另一個類別 `TestAccess`。 `BaseClass` 擁有 protected internal 成員 `myValue`，它是由 `TestAccess` 類型存取。
在第二個檔案中，嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤，而透過衍生類別 `DerivedClass` 的執行個體存取這個成員時會成功。

結構成員不可以是 `protected internal`，因為無法繼承結構。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [存取修飾詞](access-modifiers.md)
- [存取範圍層級](accessibility-levels.md)
- [修飾詞](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [internal virtual 關鍵字的安全性考量](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))