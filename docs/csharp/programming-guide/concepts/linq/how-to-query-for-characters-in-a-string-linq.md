---
title: '如何查詢字串中的字元 (LINQ)  (c # ) '
description: '您可以使用 LINQ 中的字元序列來查詢字串。 這個 c # 範例會查詢字串，以判斷其所包含的數位數位數目。'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 73288924d057e720a744b853998a52437b9db481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153933"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>如何查詢字串中的字元 (LINQ)  (c # ) 

因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。 不過，這不是常見的 LINQ 用法。 對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。  
  
## <a name="example"></a>範例  

 下列範例會查詢字串，以判斷它所包含的數字位數。 請注意，查詢會在第一次執行之後「重複使用」。 這可能是因為查詢本身不會儲存任何實際結果。  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  

 建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。  
  
## <a name="see-also"></a>另請參閱

- [LINQ 和字串 (C#)](./linq-and-strings.md)
- [如何使用正則運算式合併 LINQ 查詢 (c # ) ](./how-to-combine-linq-queries-with-regular-expressions.md)
