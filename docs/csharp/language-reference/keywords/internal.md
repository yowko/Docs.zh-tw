---
title: "internal (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
dev_langs:
- CSharp
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5674a78e2c317357c31d9e2661a25ce86cbf4f6a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="internal-c-reference"></a>internal (C# 參考)
`internal` 關鍵字是類型和類型成員的[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。 內部類型或成員只能在相同組件的檔案內存取，如下列範例所示：  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 具有存取修飾詞 `protected internal` 的類型或成員，可以從目前的組件或衍生自包含類別的類型存取。  
  
 如需 `internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 如需組件的詳細資訊，請參閱[組件和全域組件快取](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)。  
  
 內部存取常用於以元件為基礎的開發作業，因為它可讓一組元件私下相互合作，而不會公開給應用程式的其餘程式碼。 例如，建立圖形化使用者介面的架構可提供 `Control` 和 `Form` 類別，這兩個類別會以內部存取方式透過成員來相互合作。 由於這些是內部成員，因此不會公開給使用此架構的程式碼。  
  
 在定義類型或成員的組件外部，以內部存取方式來參考此類型或成員是錯誤的做法。  
  
## <a name="example"></a>範例  
 此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly1_a.cs`。 第一個檔案包含內部基底類別 `BaseClass`。 在第二個檔案中，嘗試具現化 `BaseClass` 會產生錯誤。  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
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
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
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
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)

