---
title: "保護內部 （C# 參考）"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a>保護內部 （C# 參考）
`protected internal`關鍵字的組合都是成員的存取修飾詞。 從目前的組件或型別衍生自包含類別，存取受保護內部成員。 如需 `protected internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。 
   
## <a name="example"></a>範例  
 從任何類型，其包含的組件內存取受保護內部成員的基底類別。 它也是在衍生類別位於另一個組件存取是透過衍生的類別類型的變數時，才可存取。 例如，請考慮下列程式碼區段：  

```
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
  
```  
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
 此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。 第一個檔案包含公用的基底類別， `BaseClass`，和另一個類別， `TestAccess`。 `BaseClass`擁有受保護的內部成員， `myValue`，這由存取`TestAccess`型別。 在第二個檔案中，嘗試存取`myValue`的執行個體透過`BaseClass`都會產生錯誤，透過在衍生類別的執行個體，這個成員的存取時`DerivedClass`會成功。 

 結構成員不能使用`protected internal`因為結構無法被繼承。  
  
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
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [Internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
