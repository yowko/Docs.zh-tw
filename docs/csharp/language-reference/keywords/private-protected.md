---
title: "私用受保護 （C# 參考）"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a>私用受保護 （C# 參考）
`private protected`關鍵字的組合都是成員的存取修飾詞。 型別衍生自包含類別，但只在其包含的組件內存取受保護的私用成員。 如需 `private protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。 
   
## <a name="example"></a>範例  
 只有靜態類型的變數是在衍生的類別類型從衍生類型，其包含的組件中存取私用基底類別的 protected 的成員。 例如，請考慮下列程式碼區段：  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
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
 此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。 第一個檔案包含公用的基底類別， `BaseClass`，並從其衍生的型別`DerivedClass1`。 `BaseClass`擁有私用受保護的成員， `myValue`、 哪些`DerivedClass1`嘗試存取有兩種。 第一次嘗試存取`myValue`的執行個體透過`BaseClass`都會產生錯誤。 不過，嘗試將它當做中的繼承成員`DerivedClass1`會成功。
在第二個檔案中，嘗試存取`myValue`之繼承成員`DerivedClass2`都會產生錯誤，因為它僅存取 Assembly1 內的衍生型別。 

 結構成員不能使用`private protected`因為結構無法被繼承。  
  
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
