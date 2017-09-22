---
title: "使用存取範圍層級的限制 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
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
ms.openlocfilehash: 8e49afd38fd776593b87f065a079da0d546df4a6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>使用存取範圍層級的限制 (C# 參考)
當您在宣告中指定類型時，請檢查類型的存取範圍層級是否相依於成員或另一個類型的存取範圍層級。 例如，直接基底類別至少必須可以像衍生類別一樣地存取。 下列宣告會導致編譯器錯誤，因為基底類別 `BaseClass` 比 `MyClass` 更少存取：  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 下表摘要說明所宣告存取範圍層級的限制。  
  
|內容|備註|  
|-------------|-------------|  
|[類別](../../../csharp/programming-guide/classes-and-structs/classes.md)|類別類型的直接基底類別至少必須可以像類別類型本身一樣地存取。|  
|[介面](../../../csharp/programming-guide/interfaces/index.md)|介面類型的明確基底介面至少必須可以像介面類型本身一樣地存取。|  
|[委派](../../../csharp/programming-guide/delegates/index.md)|委派類型的傳回類型和參數類型至少必須可以像委派類型本身一樣地存取。|  
|[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)|常數的類型至少必須可以像常數本身一樣地存取。|  
|[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)|欄位的類型至少必須可以像欄位本身一樣地存取。|  
|[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)|方法的傳回類型和參數類型至少必須可以像方法本身一樣地存取。|  
|[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)|屬性的類型至少必須可以像屬性本身一樣地存取。|  
|[事件](../../../csharp/programming-guide/events/index.md)|事件的類型至少必須可以像事件本身一樣地存取。|  
|[索引子](../../../csharp/programming-guide/indexers/index.md)|索引子的類型和參數類型至少必須可以像索引子本身一樣地存取。|  
|[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|運算子的傳回類型和參數類型至少必須可以像運算子本身一樣地存取。|  
|[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)|建構函式的參數類型至少必須可以像建構函式本身一樣地存取。|  
  
## <a name="example"></a>範例  
 下列範例包含不同類型的錯誤宣告。 每個宣告之後的註解都指出預期的編譯器錯誤。  
  
```  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)

