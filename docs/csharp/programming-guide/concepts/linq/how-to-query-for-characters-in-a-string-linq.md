---
title: 如何查詢字串中的字元（LINQ）（C#）
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345673"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>如何查詢字串中的字元（LINQ）（C#）
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
  
## <a name="see-also"></a>請參閱

- [LINQ 和字串 (C#)](./linq-and-strings.md)
- [如何結合 LINQ 查詢與正則運算式（C#）](./how-to-combine-linq-queries-with-regular-expressions.md)
