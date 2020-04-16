---
title: private protected - C# 參考
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463047"
---
# <a name="private-protected-c-reference"></a>private protected (C# 參考)

`private protected` 關鍵字組合是成員存取修飾詞。 從包含類別衍生的類型可以存取 private protected 成員，但只能在其包含的組件內存取。 如需 `private protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。

> [!NOTE]
> `private protected` 存取修飾詞適用於 C# 7.2 版及更新版本。

## <a name="example"></a>範例

只有當變數的靜態類型是在衍生的類別類型時，才能從包含組件的衍生類型中存取基底類別的 private protected 成員。 例如，請考慮下列程式碼區段：

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。
第一個檔案包含公用的基底類別 `BaseClass`，以及從其衍生的類型 `DerivedClass1`。 `BaseClass` 擁有 private protected 成員 `myValue`，`DerivedClass1` 會以兩種方式嘗試存取它。 第一次嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤。 不過，嘗試將它當作 `DerivedClass1` 中的繼承成員使用會成功。

在第二個檔案中，嘗試當作 `DerivedClass2` 的繼承成員存取 `myValue` 會產生錯誤，因為它只能由 Assembly1 中的衍生類型存取。

如果`Assembly1.cs`包含<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>該`Assembly2`名稱 ,則`DerivedClass1`派生類 將有`private protected``BaseClass`權訪問 在中 聲明的成員。 `InternalsVisibleTo`使`private protected`成員對其他程式集中的派生類可見。

結構成員不可以是 `private protected`，因為無法繼承結構。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [存取修飾詞](access-modifiers.md)
- [協助工具層級](accessibility-levels.md)
- [修飾詞](index.md)
- [公共](public.md)
- [私人](private.md)
- [internal](internal.md)
- [internal virtual 關鍵字的安全性考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
