---
title: private protected (C# 參考)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961128"
---
# <a name="private-protected-c-reference"></a>private protected (C# 參考)
`private protected` 關鍵字組合是成員存取修飾詞。 從包含類別衍生的類型可以存取 private protected 成員，但只能在其包含的組件內存取。 如需 `private protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。 

> [!NOTE]
> `private protected` 存取修飾詞適用於 C# 7.2 版及更新版本。
   
## <a name="example"></a>範例  
 只有當變數的靜態類型是在衍生的類別類型時，才能從包含組件的衍生類型中存取基底類別的 private protected 成員。 例如，請考慮下列程式碼區段：  
  
 ```csharp
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
 此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。 第一個檔案包含公用的基底類別 `BaseClass`，以及從其衍生的類型 `DerivedClass1`。 `BaseClass` 擁有 private protected 成員 `myValue`，`DerivedClass1` 會以兩種方式嘗試存取它。 第一次嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤。 不過，嘗試將它當作 `DerivedClass1` 中的繼承成員使用會成功。
在第二個檔案中，嘗試當作 `DerivedClass2` 的繼承成員存取 `myValue` 會產生錯誤，因為它只能由 Assembly1 中的衍生類型存取。 

 結構成員不可以是 `private protected`，因為無法繼承結構。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
