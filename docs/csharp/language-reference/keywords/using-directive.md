---
title: "using 指示詞 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e91cc4fea9fbe57b257e17915cd28b3b82f12f6e
ms.lasthandoff: 03/13/2017

---
# <a name="using-directive-c-reference"></a>using 指示詞 (C# 參考)
`using` 指示詞有三個用途：  
  
-   若要允許在命名空間中使用類型，使得您不需限定在該命名空間中使用的類型：  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   若要允許您存取類型的靜態成員，而不需以類型名稱限定存取。 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    如需詳細資訊，請參閱 [using static 指示詞](using-static.md)。

-   若要建立命名空間或類型的別名。 這稱為 *using alias 指示詞*。  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` 關鍵字也用來建立 *using 陳述式*，協助確保能夠正確處理 <xref:System.IDisposable> 物件 (例如檔案和字型)。 如需詳細資訊，請參閱 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)。  
  
## <a name="using-static-type"></a>使用靜態類型  
 您可以存取類型的靜態成員，而不需以類型名稱限定存取：  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
  
```  
  
## <a name="remarks"></a>備註  
 `using` 指示詞的範圍僅限於其出現的檔案。  
  
 建立 `using` 別名，讓您更輕鬆地將識別項限定在命名空間或類型。 using alias 指示詞的右邊一律必須是完整限定的類型，不論在它前面的 using 指示詞為何。  
  
 建立 `using` 指示詞，以在命名空間中使用類型，而無需指定命名空間。 `using` 指示詞不會授予巢狀於您指定的命名空間中的任何命名空間的存取權。  
  
 命名空間有兩種類型：使用者定義和系統定義。 使用者定義的命名空間是在程式碼中定義的命名空間。 如需系統定義的命名空間的清單，請參閱 [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=227195)。  
  
 如需參考其他組件中的方法的範例，請參閱 [Creating and Using C# DLLs](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) (建立和使用 C# DLL)。  
  
## <a name="example-1"></a>範例 1  
  
 下列範例示範如何定義和使用命名空間的 `using` 別名：  
  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 using alias 指示詞的右邊不能有開放式的泛型類型。 例如，您無法為 List\<T> 建立 using alias，但是您可以為 List\<int> 建立。  
  
## <a name="example-2"></a>範例 2  
  
 下列範例示範如何定義類別的 `using` 指示詞和 `using` 別名：  
  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [使用命名空間](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [命名空間](../../../csharp/programming-guide/namespaces/index.md)   
 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)
