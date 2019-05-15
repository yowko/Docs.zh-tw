---
title: 重構為純虛擬函式 (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3a498588e9ca1ab85602946b75b593804fa0953a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596887"
---
# <a name="refactoring-into-pure-functions-c"></a>重構為純虛擬函式 (C#)

純功能性轉換的重要觀點為學習如何使用純虛擬函式重構程式碼。  
  
> [!NOTE]
>  功能性程式設計的常見命名法為使用純虛擬函式重構程式。 在 Visual Basic 和 C++ 中，這可以利用個別的語言，調整函式的用法。 不過，在 C# 中，函式稱為方法。 就這個討論而言，純虛擬函式會當成 C# 中的方法實作。  
  
 如同本節先前所述，純虛擬函式擁有兩個實用的特性：  
  
- 它有沒有副作用。 函式不會變更函式以外任何類型的任何變數或資料。  
  
- 它是一致的。 假設是相同的輸入資料集合，就永遠會傳回相同的輸出值。  
  
 轉換為功能性程式設計的其中一種方式為重構現有的程式碼以排除不必要的副作用與外部相依性。 以此種方式，您可以建立現有程式碼的純虛擬函式版本。  
  
 這個主題討論什麼是純虛擬函式以及什麼不是純虛擬函式。 [教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) 教學課程顯示如何管理 WordprocessingML 文件，並包含兩個如何使用純虛擬函式重構的範例。  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>排除副作用與外部相依性  
 下列範例對照兩個非純虛擬函式與一個純虛擬函式。  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>變更類別成員的非純虛擬函式  
 在下列程式碼中，`HyphenatedConcat` 函式不是純虛擬函式，因為它會修改類別中的 `aMember` 資料成員：  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 此程式碼會產生下列輸出：  
  
```  
StringOne-StringTwo  
```  
  
 請注意，要修改的資料具有 `public` 或 `private` 存取權，或者是 `static` 成員或執行個體成員，都沒有關係。 純虛擬函式不會變更函式以外的任何資料。  
  
### <a name="non-pure-function-that-changes-an-argument"></a>變更引數的非純虛擬函式  
 此外，這個相同函式的下列版本不是純虛擬函式，因為它會修改其參數 `sb` 的內容。  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 這個版本的程式會產生與第一版相同的輸出，因為 `HyphenatedConcat` 函式已經叫用 <xref:System.Text.StringBuilder.Append%2A> 成員函式來變更其第一個參數的值 (狀態)。 請注意，雖然 `HyphenatedConcat` 使用 call-by-value 參數傳遞 (Parameter Passing)，還是會發生這個改變。  
  
> [!IMPORTANT]
>  若是參考型別 (Reference Type)，如果您依據值傳遞參數，會使參考的副本傳遞到物件。 這個副本仍然跟原始參考一樣，與相同的執行個體資料相關聯 (直到將參考變數指派給新的物件)。 對於要修改參數的函式，則不一定需要 Call-by-reference。  
  
### <a name="pure-function"></a>純虛擬函式  
這個下一版的程式會顯示如何將 `HyphenatedConcat` 函式實作為純虛擬函式。  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 再次聲明，這個版本會產生相同的輸出行：`StringOne-StringTwo`。 請注意，若要保留串連值，它會儲存在中繼變數 `s2` 中。  
  
 其中一個可能非常實用的方法是，撰寫在本機非純虛擬但全域為純虛擬的函式 (亦即，它們可以宣告並修改本機變數)。 這類函式擁有許多值得撰寫的特性，但是會避免某些更錯綜複雜的功能性程式設計慣用句，例如，當簡易迴圈可以完成相同的事情時，必須使用遞迴。  
  
## <a name="standard-query-operators"></a>標準查詢運算子  
 標準查詢運算子的重要特性為它們會被當做純虛擬函式實作。  
  
 如需詳細資訊，請參閱[標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [純功能性轉換簡介 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [函數式程式設計與命令式程式設計的比較 (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
