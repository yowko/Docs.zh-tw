---
title: "使用存取範圍層級的限制 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取修飾詞 [C#], 存取範圍層級的限制"
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 使用存取範圍層級的限制 (C# 參考)
當您在宣告中指定型別時，請檢查型別的存取範圍層級是否相依於某個成員或其他型別的存取範圍層級。  例如，直接基底類別 \(Base Class\) 至少必須像衍生類別那樣可存取。  下列宣告會產生編譯器 \(Compiler\) 錯誤，因為基底類別 `BaseClass` 比 `MyClass` 更不容易存取：  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 下表摘要宣告存取範圍層級的限制。  
  
|內容|備註|  
|--------|--------|  
|[類別](../../../csharp/programming-guide/classes-and-structs/classes.md)|類別型別的直接基底類別至少必須像類別型別本身那樣可存取。|  
|[介面](../../../csharp/programming-guide/interfaces/index.md)|介面型別的明確基底介面至少必須像介面型別本身那樣可存取。|  
|[委派](../../../csharp/programming-guide/delegates/index.md)|委派型別 \(Delegate Type\) 的傳回型別 \(Return Type\) 和參數型別至少必須像委派型別本身那樣可存取。|  
|[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)|常數的型別至少必須像常數本身那樣可存取。|  
|[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)|欄位的型別至少必須像欄位本身那樣可存取。|  
|[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)|方法的傳回型別和參數型別必須至少像方法本身那樣可存取。|  
|[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)|屬性的型別至少必須像屬性本身那樣可存取。|  
|[事件](../../../csharp/programming-guide/events/index.md)|事件的型別至少必須像事件本身那樣可存取。|  
|[索引子](../../../csharp/programming-guide/indexers/index.md)|索引子 \(Indexer\) 的型別和參數型別至少必須像索引子本身那樣可存取。|  
|[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|運算子的傳回型別和參數型別至少必須像運算子本身那樣可存取。|  
|[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)|建構函式的參數型別至少必須像建構函式本身那樣可存取。|  
  
## 範例  
 下列範例包含不同型別的錯誤宣告。  每一個宣告之後的註解指出預期的編譯器錯誤。  
  
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
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)