---
title: internal (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523357"
---
# <a name="internal-c-reference"></a>internal (C# 參考)
`internal` 關鍵字是類型和類型成員的[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。 
  
 > 此頁面涵蓋 `internal` 存取。 `internal` 關鍵字也是屬於 [`protected internal`](./protected-internal.md) 存取修飾詞。
  
內部類型或成員只能在相同組件的檔案內存取，如下列範例所示：  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 如需 `internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 如需組件的詳細資訊，請參閱[組件和全域組件快取](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)。  
  
 內部存取常用於以元件為基礎的開發作業，因為它可讓一組元件私下相互合作，而不會公開給應用程式的其餘程式碼。 例如，建立圖形化使用者介面的架構可提供 `Control` 和 `Form` 類別，這兩個類別會以內部存取方式透過成員來相互合作。 由於這些是內部成員，因此不會公開給使用此架構的程式碼。  
  
 在定義類型或成員的組件外部，以內部存取方式來參考此類型或成員是錯誤的做法。  
  
## <a name="example"></a>範例  
 此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly1_a.cs`。 第一個檔案包含內部基底類別 `BaseClass`。 在第二個檔案中，嘗試具現化 `BaseClass` 會產生錯誤。  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>範例  
 在此範例中，請使用您在範例 1 中所用的相同檔案，並將 `BaseClass` 的存取範圍層級變更為 `public`。 同時將成員 `IntM` 的存取範圍層級變更為 `internal`。 在此情況下，您可以具現化類別，但無法存取內部成員。  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
- [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)
