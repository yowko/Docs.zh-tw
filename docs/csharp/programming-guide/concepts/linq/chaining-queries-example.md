---
title: 鏈結查詢範例 (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205423"
---
# <a name="chaining-queries-example-c"></a>鏈結查詢範例 (C#)
這個範例會在先前的範例上建置，然後在將同時使用延後執行與延遲評估的兩個查詢鏈結在一起時，顯示發生什麼狀況。  
  
## <a name="example"></a>範例  
 在此範例中，會介紹另一個擴充方法 `AppendString`，這個擴充方法會將指定的字串附加到來源集合中的每個字串，然後產生新的字串。  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 這個範例會產生下列輸出：  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 在此範例中，您可以看到每個擴充方法會針對來源集合中的每個項目，一次運算一個。  
  
 從這個範例應該清楚知道的是，即使我們已經將產生集合的查詢鏈結在一起，還是不會具體化任何中繼集合。 但是，每個項目都會從一個延遲方法傳遞到下一個延遲方法。 這會使記憶體使用量比先取得一個字串陣列，然後建立已經轉換為大寫的另一個字串陣列，最後建立每個字串都已經附加驚嘆號的第三個字串陣列這種方法小很多。  
  
 本教學課程中的下一個主題說明中繼具體化：  
  
- [中繼具體化 (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>另請參閱

- [教學課程：將查詢鏈結在一起 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
